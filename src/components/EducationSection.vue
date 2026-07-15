<script setup lang="ts">
import { education, activities } from '@/data/portfolio'
</script>

<template>
  <section id="education" class="section">
    <div class="container">
      <div
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 600 } }"
      >
        <p class="section-label">Background</p>
        <h2 class="section-title">Education & Activities</h2>
      </div>

      <div class="edu-grid">
        <div class="edu-column">
          <h3 class="column-title">Education</h3>
          <div
            v-for="(item, index) in education"
            :key="item.degree"
            v-motion
            :initial="{ opacity: 0, x: -30 }"
            :visibleOnce="{ opacity: 1, x: 0, transition: { duration: 500, delay: index * 120 } }"
            class="edu-card glass-card"
          >
            <span class="edu-period">{{ item.period }}</span>
            <h4>{{ item.degree }}</h4>
            <p>{{ item.school }}</p>
          </div>
        </div>

        <div class="edu-column">
          <h3 class="column-title">Activities</h3>
          <div
            v-for="(item, index) in activities"
            :key="item.title"
            v-motion
            :initial="{ opacity: 0, x: 30 }"
            :visibleOnce="{ opacity: 1, x: 0, transition: { duration: 500, delay: index * 120 } }"
            class="edu-card glass-card"
          >
            <h4>{{ item.title }}</h4>
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.edu-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2.5rem;
}

.column-title {
  font-size: 1.1rem;
  color: var(--color-accent);
  margin-bottom: 1.25rem;
  font-family: var(--font-mono);
}

.edu-column {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.edu-card {
  padding: 1.5rem;
}

.edu-period {
  display: inline-block;
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: var(--color-text-muted);
  margin-bottom: 0.5rem;
}

.edu-card h4 {
  font-size: 1.05rem;
  margin-bottom: 0.35rem;
}

.edu-card p {
  color: var(--color-text-muted);
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .edu-grid {
    grid-template-columns: 1fr;
  }
}
</style>
