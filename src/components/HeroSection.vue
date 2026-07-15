<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { profile } from '@/data/portfolio'

const roles = ['Software Engineer', 'Backend Developer', 'Web Developer', 'Full-Stack Developer']
const currentRole = ref('')
const roleIndex = ref(0)
const charIndex = ref(0)
const isDeleting = ref(false)

const typeEffect = () => {
  const role = roles[roleIndex.value]!
  if (!isDeleting.value) {
    currentRole.value = role.slice(0, charIndex.value + 1)
    charIndex.value++
    if (charIndex.value === role.length) {
      setTimeout(() => {
        isDeleting.value = true
      }, 2000)
    }
  } else {
    currentRole.value = role.slice(0, charIndex.value - 1)
    charIndex.value--
    if (charIndex.value === 0) {
      isDeleting.value = false
      roleIndex.value = (roleIndex.value + 1) % roles.length
    }
  }
}

onMounted(() => {
  const tick = () => {
    typeEffect()
    setTimeout(tick, isDeleting.value ? 60 : 100)
  }
  tick()
})
</script>

<template>
  <section id="home" class="hero section">
    <div class="bg-grid" />
    <div class="bg-glow glow-1" />
    <div class="bg-glow glow-2" />

    <div class="container hero-content">
      <div
        v-motion
        :initial="{ opacity: 0, y: 30 }"
        :enter="{ opacity: 1, y: 0, transition: { duration: 600 } }"
        class="hero-badge"
      >
        <span class="pulse" />
        Available for opportunities
      </div>

      <h1
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :enter="{ opacity: 1, y: 0, transition: { duration: 700, delay: 100 } }"
        class="hero-name"
      >
        Hi, I'm <span class="gradient-text">{{ profile.name }}</span>
      </h1>

      <p
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :enter="{ opacity: 1, y: 0, transition: { duration: 700, delay: 200 } }"
        class="hero-role"
      >
        {{ currentRole }}<span class="cursor">|</span>
      </p>

      <p
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :enter="{ opacity: 1, y: 0, transition: { duration: 700, delay: 300 } }"
        class="hero-location"
      >
        📍 {{ profile.location }}
      </p>

      <div
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :enter="{ opacity: 1, y: 0, transition: { duration: 700, delay: 400 } }"
        class="hero-actions"
      >
        <a href="#projects" class="btn btn-primary">View My Work</a>
        <a href="#contact" class="btn btn-outline">Get In Touch</a>
        <a :href="profile.github" target="_blank" rel="noopener" class="btn btn-outline">
          GitHub ↗
        </a>
      </div>

      <div
        v-motion
        :initial="{ opacity: 0 }"
        :enter="{ opacity: 1, transition: { duration: 800, delay: 700 } }"
        class="scroll-indicator"
      >
        <span>Scroll</span>
        <div class="scroll-line" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding-top: var(--nav-height);
  overflow: hidden;
}

.glow-1 {
  width: 500px;
  height: 500px;
  background: #6366f1;
  top: -100px;
  right: -100px;
  animation: float 8s ease-in-out infinite;
}

.glow-2 {
  width: 400px;
  height: 400px;
  background: #22d3ee;
  bottom: 0;
  left: -100px;
  animation: float 10s ease-in-out infinite reverse;
}

@keyframes float {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(30px, -30px);
  }
}

.hero-content {
  position: relative;
  z-index: 1;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.4rem 1rem;
  font-size: 0.85rem;
  color: var(--color-accent);
  background: var(--color-accent-soft);
  border: 1px solid rgba(34, 211, 238, 0.25);
  border-radius: 999px;
  margin-bottom: 1.5rem;
}

.pulse {
  width: 8px;
  height: 8px;
  background: #22d3ee;
  border-radius: 50%;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 1;
    transform: scale(1);
  }
  50% {
    opacity: 0.5;
    transform: scale(1.3);
  }
}

.hero-name {
  font-size: clamp(2.5rem, 7vw, 4.5rem);
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -0.03em;
  margin-bottom: 1rem;
}

.gradient-text {
  background: var(--gradient-text);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-role {
  font-size: clamp(1.25rem, 3vw, 1.75rem);
  color: var(--color-text-muted);
  font-family: var(--font-mono);
  margin-bottom: 0.75rem;
  min-height: 2.5rem;
}

.cursor {
  color: var(--color-accent);
  animation: blink 1s step-end infinite;
}

@keyframes blink {
  50% {
    opacity: 0;
  }
}

.hero-location {
  color: var(--color-text-muted);
  margin-bottom: 2rem;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 4rem;
}

.scroll-indicator {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  color: var(--color-text-muted);
  font-size: 0.75rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
}

.scroll-line {
  width: 1px;
  height: 48px;
  background: linear-gradient(to bottom, var(--color-accent), transparent);
  animation: scrollDown 2s ease-in-out infinite;
}

@keyframes scrollDown {
  0% {
    transform: scaleY(0);
    transform-origin: top;
  }
  50% {
    transform: scaleY(1);
    transform-origin: top;
  }
  51% {
    transform: scaleY(1);
    transform-origin: bottom;
  }
  100% {
    transform: scaleY(0);
    transform-origin: bottom;
  }
}
</style>
