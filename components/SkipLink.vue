<template>
  <nuxt-link class="skip-link" to="#main-content">
    Skip to main content</nuxt-link
  >
</template>

<style scoped>
.skip-link {
  padding: 4px;
  position: absolute;
  left: 2em;
  font-weight: 700;
  transform: translateY(-100%);
  color: var(--text-primary);
  background: var(--text-contrast);
  z-index: 999;
}
@media (prefers-reduced-motion: no-preference) {
  /* enable animation for users without reduced motion preference */
  .skip-link {
    transition: transform 0.3s;
  }
}
.skip-link:focus {
  transform: translateY(0%);
}
</style>
