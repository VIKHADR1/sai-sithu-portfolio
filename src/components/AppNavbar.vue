<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { navLinks } from '@/data/portfolio'

const isScrolled = ref(false)
const activeSection = ref('home')
const mobileOpen = ref(false)

const scrollTo = (id: string) => {
  mobileOpen.value = false
  const el = document.getElementById(id)
  el?.scrollIntoView({ behavior: 'smooth' })
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 40

  const sections = navLinks.map((l) => l.id)
  for (const id of [...sections].reverse()) {
    const el = document.getElementById(id)
    if (el && window.scrollY >= el.offsetTop - 120) {
      activeSection.value = id
      break
    }
  }
}

onMounted(() => window.addEventListener('scroll', handleScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="navbar-inner container">
      <button class="logo" @click="scrollTo('home')">
        <span class="logo-bracket">&lt;</span>SSP<span class="logo-bracket">/&gt;</span>
      </button>

      <button class="menu-toggle" aria-label="Toggle menu" @click="mobileOpen = !mobileOpen">
        <span :class="{ open: mobileOpen }" />
        <span :class="{ open: mobileOpen }" />
        <span :class="{ open: mobileOpen }" />
      </button>

      <ul class="nav-links" :class="{ open: mobileOpen }">
        <li v-for="link in navLinks" :key="link.id">
          <button
            :class="{ active: activeSection === link.id }"
            @click="scrollTo(link.id)"
          >
            {{ link.label }}
          </button>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  height: var(--nav-height);
  transition: background 0.35s ease, box-shadow 0.35s ease, backdrop-filter 0.35s ease;
}

.navbar.scrolled {
  background: rgba(7, 11, 20, 0.85);
  backdrop-filter: blur(16px);
  box-shadow: 0 1px 0 var(--color-border);
}

.navbar-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
}

.logo {
  font-family: var(--font-mono);
  font-size: 1.25rem;
  font-weight: 700;
  color: #f8fafc;
  background: none;
  border: none;
  cursor: pointer;
}

.logo-bracket {
  color: var(--color-accent);
}

.nav-links {
  display: flex;
  gap: 0.25rem;
  list-style: none;
}

.nav-links button {
  background: none;
  border: none;
  color: var(--color-text-muted);
  font-size: 0.9rem;
  font-weight: 500;
  padding: 0.5rem 0.85rem;
  border-radius: 999px;
  cursor: pointer;
  transition: color 0.25s ease, background 0.25s ease;
}

.nav-links button:hover,
.nav-links button.active {
  color: #f8fafc;
  background: rgba(99, 102, 241, 0.12);
}

.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}

.menu-toggle span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--color-text);
  transition: transform 0.3s ease, opacity 0.3s ease;
}

.menu-toggle span:nth-child(1).open {
  transform: translateY(7px) rotate(45deg);
}

.menu-toggle span:nth-child(2).open {
  opacity: 0;
}

.menu-toggle span:nth-child(3).open {
  transform: translateY(-7px) rotate(-45deg);
}

@media (max-width: 768px) {
  .menu-toggle {
    display: flex;
  }

  .nav-links {
    position: fixed;
    top: var(--nav-height);
    left: 0;
    right: 0;
    flex-direction: column;
    background: rgba(7, 11, 20, 0.97);
    backdrop-filter: blur(16px);
    padding: 1rem;
    border-bottom: 1px solid var(--color-border);
    transform: translateY(-120%);
    opacity: 0;
    pointer-events: none;
    transition: transform 0.35s ease, opacity 0.35s ease;
  }

  .nav-links.open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .nav-links button {
    width: 100%;
    text-align: left;
    padding: 0.85rem 1rem;
  }
}
</style>
