<script setup lang="ts">
import { experience } from '@/data/portfolio'
</script>

<template>
  <section id="experience" class="section">
    <div class="container">
      <div
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 600 } }"
      >
        <p class="section-label">Career</p>
        <h2 class="section-title">Work Experience</h2>
      </div>

      <div class="timeline">
        <div
          v-for="(job, index) in experience"
          :key="job.company"
          v-motion
          :initial="{ opacity: 0, x: index % 2 === 0 ? -40 : 40 }"
          :visibleOnce="{ opacity: 1, x: 0, transition: { duration: 600, delay: index * 150 } }"
          class="timeline-item glass-card"
        >
          <div class="timeline-marker" />
          <div class="timeline-header">
            <div>
              <h3>{{ job.role }}</h3>
              <p class="company">{{ job.company }}</p>
            </div>
            <span class="period">{{ job.period }}</span>
          </div>
          <ul>
            <li v-for="(item, i) in job.highlights" :key="i">{{ item }}</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.timeline {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding-left: 2rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(to bottom, var(--color-primary), var(--color-accent), transparent);
}

.timeline-item {
  position: relative;
  padding: 1.75rem 2rem;
}

.timeline-marker {
  position: absolute;
  left: -2rem;
  top: 2rem;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: var(--color-accent);
  border: 3px solid var(--color-bg);
  transform: translateX(-6px);
  box-shadow: 0 0 12px rgba(34, 211, 238, 0.5);
}

.timeline-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 1rem;
  margin-bottom: 1rem;
  flex-wrap: wrap;
}

.timeline-header h3 {
  font-size: 1.2rem;
  margin-bottom: 0.25rem;
}

.company {
  color: var(--color-primary-light);
  font-weight: 500;
}

.period {
  font-family: var(--font-mono);
  font-size: 0.85rem;
  color: var(--color-text-muted);
  white-space: nowrap;
  padding: 0.35rem 0.75rem;
  background: rgba(239, 131, 84, 0.1);
  border-radius: 999px;
}

.timeline-item ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.timeline-item li {
  color: var(--color-text-muted);
  font-size: 0.95rem;
  padding-left: 1.25rem;
  position: relative;
}

.timeline-item li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--color-accent);
}

@media (max-width: 768px) {
  .timeline {
    padding-left: 1.5rem;
  }

  .timeline-marker {
    left: -1.5rem;
  }
}
</style>
