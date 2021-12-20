<template>
  <main id="main-content">
    <section class="intro">
      <div class="intro__content">
        <h1>Brain Covid</h1>
        <p class="intro__subtitle">Data sharing and collaboration initiative</p>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi natus
          ratione laudantium, impedit, itaque enim consectetur deserunt ab
          assumenda fugit molestias numquam repudiandae in autem dignissimos
          mollitia, sunt optio a!
        </p>
        <div class="intro__links">
          <nuxt-link class="button" to="/mri/">MRI results</nuxt-link>
          <nuxt-link class="button" to="/histology/"
            >Histology results</nuxt-link
          >
          <nuxt-link class="" to="/about/"
            >Learn more about this projet</nuxt-link
          >
        </div>
      </div>
      <div class="intro__image">
        <nuxt-picture
          class="hp-intro__image"
          src="/homepage/brain-icon.jpg"
          sizes="sm:100vw xl:470px"
          alt=""
          width="470"
          height="410"
          quality="92"
        />
      </div>
    </section>
  </main>
</template>

<style scoped>
.intro {
  margin: 2rem auto;
  max-width: 100rem;
  /* header height and margins */
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(46.2rem, 100%), 1fr));
  gap: 6rem;
  align-items: center;
}
.intro h1 {
  margin: 0;
}
.intro__subtitle {
  font-size: clamp(2.6rem, 2.4rem + 0.625vw, 3.2rem);
  font-weight: 300;
}
.intro__links {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.intro__links > * {
  margin: 0;
}
.intro__links > * + * {
  margin-top: 1.6rem;
}

@media screen and (min-width: 1024px) {
  .intro {
    min-height: calc(100vh - 7.6rem - 4rem);
  }
}
</style>
