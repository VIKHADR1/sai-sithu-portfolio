<script setup lang="ts">
import { skills } from '@/data/portfolio'

const categories = [
  { key: 'languages' as const, label: 'Programming Languages', icon: '💻' },
  { key: 'databases' as const, label: 'Databases', icon: '🗄️' },
  { key: 'soft' as const, label: 'Soft Skills', icon: '🤝' },
]
</script>

<template>
  <section id="skills" class="section">
    <div class="container">
      <div
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 600 } }"
      >
        <p class="section-label">Expertise</p>
        <h2 class="section-title">Technical Skills</h2>
      </div>

      <div class="skills-grid">
        <div
          v-for="(cat, index) in categories"
          :key="cat.key"
          v-motion
          :initial="{ opacity: 0, scale: 0.9 }"
          :visibleOnce="{ opacity: 1, scale: 1, transition: { duration: 500, delay: index * 100 } }"
          class="skill-group glass-card"
        >
          <div class="skill-header">
            <span class="skill-icon">{{ cat.icon }}</span>
            <h3>{{ cat.label }}</h3>
          </div>
          <div class="skill-tags">
            <span
              v-for="(skill, i) in skills[cat.key]"
              :key="skill"
              v-motion
              :initial="{ opacity: 0, y: 10 }"
              :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 400, delay: index * 100 + i * 60 } }"
              class="skill-tag"
            >
              {{ skill }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.skill-group {
  padding: 1.75rem;
}

.skill-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1.25rem;
}

.skill-icon {
  font-size: 1.5rem;
}

.skill-header h3 {
  font-size: 1.1rem;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.skill-tag {
  padding: 0.5rem 1rem;
  font-size: 0.85rem;
  color: var(--color-text);
  background: rgba(99, 102, 241, 0.08);
  border: 1px solid rgba(99, 102, 241, 0.2);
  border-radius: var(--radius-lg);
  transition: background 0.25s ease, border-color 0.25s ease, transform 0.25s ease;
}

.skill-tag:hover {
  background: rgba(99, 102, 241, 0.15);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-2px);
}
</style>
