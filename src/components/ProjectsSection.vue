<script setup lang="ts">
import { projects } from '@/data/portfolio'
</script>

<template>
  <section id="projects" class="section">
    <div class="bg-glow glow" />
    <div class="container">
      <div
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 600 } }"
      >
        <p class="section-label">Portfolio</p>
        <h2 class="section-title">Featured Projects</h2>
      </div>

      <div class="projects-grid">
        <article
          v-for="(project, index) in projects"
          :key="project.title"
          v-motion
          :initial="{ opacity: 0, y: 50 }"
          :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 600, delay: index * 120 } }"
          class="project-card glass-card"
        >
          <div class="project-icon">{{ project.icon }}</div>
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
          <div class="tags">
            <span v-for="tech in project.technologies" :key="tech" class="tag">{{ tech }}</span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.section {
  position: relative;
  overflow: hidden;
}

.glow {
  width: 600px;
  height: 600px;
  background: #a855f7;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  opacity: 0.2;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.project-card {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.project-icon {
  font-size: 2.5rem;
  line-height: 1;
}

.project-card h3 {
  font-size: 1.25rem;
}

.project-card p {
  color: var(--color-text-muted);
  font-size: 0.95rem;
  line-height: 1.7;
  flex: 1;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 0.5rem;
}
</style>
