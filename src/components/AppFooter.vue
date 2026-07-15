<script setup lang="ts">
import { profile } from '@/data/portfolio'

const year = new Date().getFullYear()
</script>

<template>
  <footer class="footer">
    <div class="container footer-inner">
      <p>
        &copy; {{ year }} <strong>{{ profile.name }}</strong>. Built with Vue.js
      </p>
      <div class="footer-links">
        <a :href="profile.github" target="_blank" rel="noopener">GitHub</a>
        <a :href="`mailto:${profile.email}`">Email</a>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  padding: 2rem 0;
  border-top: 1px solid var(--color-border);
}

.footer-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
  color: var(--color-text-muted);
  font-size: 0.9rem;
}

.footer-inner strong {
  color: var(--color-text);
}

.footer-links {
  display: flex;
  gap: 1.5rem;
}

.footer-links a {
  color: var(--color-text-muted);
  text-decoration: none;
  transition: color 0.25s ease;
}

.footer-links a:hover {
  color: var(--color-accent);
}
</style>
