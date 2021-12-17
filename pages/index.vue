<template>
  <main id="main-content">
    <section class="intro">
      <div class="intro__content">
        <h1>Brain Covid</h1>
        <p>Data sharing and collaboration initiative</p>
        <nuxt-link class="button" to="/patients/">Discover the cases</nuxt-link>
      </div>
      <div class="intro__image">
        <nuxt-picture
          class="hp-intro__image"
          src="/homepage/brain-icon.jpg"
          sizes="sm:100vw xl:600px"
          alt=""
          width="600"
          height="600"
          quality="92"
        />
      </div>
    </section>
  </main>
</template>

<style scoped>
.intro {
  margin: 0 auto;
  max-width: 100rem;
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  align-items: center;
}
.intro h1 {
  margin: 0;
}
</style>
