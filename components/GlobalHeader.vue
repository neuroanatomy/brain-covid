<template>
  <header>
    <skip-link />
    <div class="header">
      <nuxt-link class="header__logo" to="/">Brain Covid</nuxt-link>
      <nav aria-label="Main">
        <ul class="header__nav" clean-list>
          <li>
            <nuxt-link to="/">Home</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/mri/">MRI</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/histology/">Histology</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/about/">About</nuxt-link>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {}
</script>

<style scoped>
.header {
  padding: 2rem 0;
  position: relative;
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  align-items: baseline;
}
.header::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 2px;
  border-radius: 8px;
  background-color: var(--accent);
}
.header__logo {
  font-size: 2.4rem;
  font-weight: bold;
  text-decoration: none;
  color: var(--text-contrast);
}
.header__nav {
  display: flex;
  flex-flow: row wrap;
  gap: 2rem;
}
</style>
