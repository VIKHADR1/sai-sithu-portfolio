<script setup lang="ts">
import { profile } from '@/data/portfolio'
</script>

<template>
  <section id="contact" class="section">
    <div class="bg-glow glow" />
    <div class="container">
      <div
        v-motion
        :initial="{ opacity: 0, y: 40 }"
        :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 600 } }"
        class="contact-wrapper glass-card"
      >
        <p class="section-label">Contact</p>
        <h2 class="section-title">Let's Work Together</h2>
        <p class="contact-text">
          I'm currently open to web developer opportunities. Feel free to reach out — I'd love to
          hear from you!
        </p>

        <div
          v-motion
          :initial="{ opacity: 0, y: 20 }"
          :visibleOnce="{ opacity: 1, y: 0, transition: { duration: 500, delay: 200 } }"
          class="contact-links"
        >
          <a :href="`mailto:${profile.email}`" class="contact-item">
            <span class="contact-icon">📧</span>
            <div>
              <span class="contact-label">Email</span>
              <span class="contact-value">{{ profile.email }}</span>
            </div>
          </a>
          <a :href="`tel:${profile.phone}`" class="contact-item">
            <span class="contact-icon">📱</span>
            <div>
              <span class="contact-label">Phone</span>
              <span class="contact-value">{{ profile.phone }}</span>
            </div>
          </a>
          <a :href="profile.github" target="_blank" rel="noopener" class="contact-item">
            <span class="contact-icon">🔗</span>
            <div>
              <span class="contact-label">GitHub</span>
              <span class="contact-value">github.com/SaiSithuPhyo</span>
            </div>
          </a>
          <div class="contact-item">
            <span class="contact-icon">📍</span>
            <div>
              <span class="contact-label">Location</span>
              <span class="contact-value">{{ profile.location }}</span>
            </div>
          </div>
        </div>

        <a
          v-motion
          :initial="{ opacity: 0, scale: 0.9 }"
          :visibleOnce="{ opacity: 1, scale: 1, transition: { duration: 500, delay: 400 } }"
          :href="`mailto:${profile.email}?subject=Job Opportunity - Web Developer`"
          class="btn btn-primary contact-btn"
        >
          Send Me an Email
        </a>
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
  width: 500px;
  height: 500px;
  background: var(--color-primary);
  bottom: -200px;
  right: -100px;
  opacity: 0.25;
}

.contact-wrapper {
  padding: 3rem;
  text-align: center;
  position: relative;
  z-index: 1;
}

.contact-text {
  color: var(--color-text-muted);
  max-width: 520px;
  margin: -1.5rem auto 2.5rem;
  font-size: 1.05rem;
}

.contact-links {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1rem;
  margin-bottom: 2.5rem;
  text-align: left;
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1.25rem;
  background: rgba(114, 143, 225, 0.08);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  text-decoration: none;
  color: inherit;
  transition:
    border-color 0.25s ease,
    background 0.25s ease,
    transform 0.25s ease;
  min-width: 0;
}

.contact-item:hover {
  border-color: rgba(153, 159, 225, 0.35);
  background: rgba(35, 47, 80, 0.12);
  transform: translateY(-2px);
}

.contact-icon {
  font-size: 1.5rem;
  flex-shrink: 0;
  line-height: 1;
}

.contact-label {
  display: block;
  font-size: 0.75rem;
  color: var(--color-text-muted);
  text-transform: uppercase;
  letter-spacing: 0.06em;
  margin-bottom: 0.15rem;
}

.contact-value {
  display: block;
  font-size: 0.9rem;
  color: var(--color-text);
  overflow-wrap: anywhere;
  word-break: break-word;
  white-space: normal;
}

.contact-btn {
  font-size: 1rem;
  padding: 1rem 2.5rem;
}

@media (max-width: 768px) {
  .contact-wrapper {
    padding: 2rem 1.5rem;
  }
}
</style>
