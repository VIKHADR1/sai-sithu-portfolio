<script setup lang="ts">
import { profile } from '@/data/portfolio'
</script>

<template>
  <section id="about" class="section">
    <div class="container">
      <div
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 600 } }"
      >
        <p class="section-label">About Me</p>
        <h2 class="section-title">Professional Summary</h2>
      </div>

      <div class="about-grid">
        <div
          v-motion
          :initial="{ opacity: 0, x: -40 }"
          :visibleOnce="{ opacity: 1, x: 0, transition: { duration: 600, delay: 100 } }"
          class="about-card glass-card"
        >
          <div class="avatar">
            <span>{{ profile.name.split(' ').map((n) => n[0]).join('') }}</span>
          </div>
          <h3>{{ profile.name }}</h3>
          <p class="subtitle">{{ profile.title }}</p>
          <ul class="contact-list">
            <li>📍 {{ profile.location }}</li>
            <li>📧 {{ profile.email }}</li>
            <li>📱 {{ profile.phone }}</li>
            <li>
              <a :href="profile.github" target="_blank" rel="noopener">🔗 GitHub Profile</a>
            </li>
          </ul>
        </div>

        <div
          v-motion
          :initial="{ opacity: 0, x: 40 }"
          :visibleOnce="{ opacity: 1, x: 0, transition: { duration: 600, delay: 200 } }"
          class="summary-card glass-card"
        >
          <p>{{ profile.summary }}</p>
          <div class="stats">
            <div class="stat">
              <span class="stat-number">3+</span>
              <span class="stat-label">Years Experience</span>
            </div>
            <div class="stat">
              <span class="stat-number">3</span>
              <span class="stat-label">Major Projects</span>
            </div>
            <div class="stat">
              <span class="stat-number">5+</span>
              <span class="stat-label">Technologies</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1.6fr;
  gap: 2rem;
  align-items: start;
}

.about-card {
  padding: 2rem;
  text-align: center;
}

.avatar {
  width: 100px;
  height: 100px;
  margin: 0 auto 1.25rem;
  border-radius: 50%;
  background: var(--gradient-hero);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  font-weight: 700;
  color: #fff;
  box-shadow: 0 8px 32px rgba(239, 131, 84, 0.28);
}

.about-card h3 {
  font-size: 1.35rem;
  margin-bottom: 0.25rem;
}

.subtitle {
  color: var(--color-text-muted);
  font-size: 0.95rem;
  margin-bottom: 1.5rem;
}

.contact-list {
  list-style: none;
  text-align: left;
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
  font-size: 0.9rem;
  color: var(--color-text-muted);
}

.contact-list a {
  color: var(--color-accent);
  text-decoration: none;
}

.contact-list a:hover {
  text-decoration: underline;
}

.summary-card {
  padding: 2rem;
}

.summary-card p {
  color: var(--color-text-muted);
  font-size: 1.05rem;
  line-height: 1.8;
  margin-bottom: 2rem;
}

.stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  padding-top: 1.5rem;
  border-top: 1px solid var(--color-border);
}

.stat {
  text-align: center;
}

.stat-number {
  display: block;
  font-size: 2rem;
  font-weight: 700;
  background: var(--gradient-text);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.stat-label {
  font-size: 0.8rem;
  color: var(--color-text-muted);
}

@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
  }

  .stats {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}
</style>
