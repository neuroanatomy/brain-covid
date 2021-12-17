<template>
  <main id="main-content">
    <h1>MRIs of patient {{ patient.id }}</h1>
    <div class="mri__toc">
      <strong>Jump to:</strong>
      <nav aria-label="Quick access">
        <ul class="toc__list" clean-list>
          <li v-for="link of mriItems" :key="link.id">
            <NuxtLink :to="`#${link.sequence}`"
              >{{ link.sequence }} - {{ link.comments }}</NuxtLink
            >
          </li>
        </ul>
      </nav>
    </div>
    <article
      v-for="mri of mriItems"
      :id="mri.sequence"
      :key="mri.id"
      class="mri__content"
    >
      <h2 class="mri__title">
        {{ mri.sequence }} - <span>{{ mri.comments }}</span>
      </h2>
      <iframe
        sandbox="allow-same-origin allow-scripts"
        :src="`https://brainbox.pasteur.fr/mri?url=${mri.url}`"
        class="patient__mri"
        width="1310"
        height="600"
        frameborder="0"
        loading="lazy"
      ></iframe>
    </article>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    const slug = params.slug
    const patient = await $content('patients', slug)
      .fetch()
      .catch((err) => {
        error({ statusCode: 404, message: 'Page not found' })
        console.log(err)
      })

    return { patient }
  },
  computed: {
    mriItems() {
      const data = this.patient.data
      return data.filter((item) => {
        return item.type === 'MRI'
      })
    },
  },
}
</script>

<style>
.mri__toc {
  margin: 4rem 0;
  padding: 2rem;
  border-radius: 8px;
  background-color: var(--accent-dark);
}
.toc__list {
  margin-top: 1.4rem;
  display: flex;
  flex-flow: row wrap;
  gap: 1.6rem;
}
.mri__content + .mri__content {
  margin-top: 8rem;
}
.patient__mri {
  min-height: 60rem;
}
.mri__title {
  margin-bottom: 2rem;
}
</style>
