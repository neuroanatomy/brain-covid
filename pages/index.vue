<template>
  <main id="main-content">
    <section class="hp-intro">
      <div class="hp-intro__content">
        <h1>Brain Covid</h1>
        <p class="hp-intro__subtitle">
          Data sharing and collaboration initiative
        </p>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi natus
          ratione laudantium, impedit, itaque enim consectetur deserunt ab
          assumenda fugit molestias numquam repudiandae in autem dignissimos
          mollitia, sunt optio a!
        </p>
        <div class="hp-intro__links">
          <nuxt-link class="button" to="/mri/">MRI data</nuxt-link>
          <nuxt-link class="button" to="/histology/">Histology data</nuxt-link>
          <nuxt-link class="" to="/about/"
            >Learn more about this projet</nuxt-link
          >
        </div>
      </div>
      <div class="hp-intro__image">
        <nuxt-picture
          class="hp-intro__image"
          src="/homepage/human-brain-color.png"
          sizes="sm:100vw xl:400px"
          alt=""
          width="400"
          height="500"
        />
      </div>
    </section>
  </main>
</template>

<style scoped>
.hp-intro {
  margin: 4rem auto 2rem;
  max-width: 120rem;
  display: grid;
  grid-template-columns: 3fr 2fr;
  align-items: center;
  justify-content: space-between;
  gap: 6rem;
}
.hp-intro h1 {
  margin: 0;
}
.hp-intro__subtitle {
  font-size: clamp(2.6rem, 2.4rem + 0.625vw, 3.2rem);
  font-weight: 300;
}
.hp-intro__links {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.hp-intro__links > * {
  margin: 0;
}
.hp-intro__links > * + * {
  margin-top: 1.6rem;
}
.hp-intro__image {
  position: relative;
  justify-self: center;
}
/* .hp-intro__image::after {
  content: '';
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  mask-image: url(@/assets/images/homepage/human-brain-mask.png);
  background-color: var(--accent);
  z-index: -1;
}
.hp-intro__image ::v-deep img {
  mix-blend-mode: luminosity;
} */

@media screen and (min-width: 1024px) {
  .hp-intro {
    /* header height and margins */
    min-height: calc(100vh - 7.6rem - 6rem);
  }
}
</style>
