<template>
  <main id="main-content">
    <h1>Histology of patient {{ patient.id }}</h1>
    <div class="histology__toc">
      <strong>Jump to:</strong>
      <nav aria-label="Quick access">
        <ul class="toc__list" clean-list>
          <li v-for="link of histologyItem" :key="link.id">
            <NuxtLink :to="`#${link.sequence}`"
              >{{ link.sequence }} - {{ link.comments }}</NuxtLink
            >
          </li>
        </ul>
      </nav>
    </div>
    <article
      v-for="histology of histologyItem"
      :id="histology.sequence"
      :key="histology.id"
      class="histology__content"
    >
      <h2 class="histology__title">
        {{ histology.sequence }} - <span>{{ histology.comments }}</span>
      </h2>
      <iframe
        sandbox="allow-same-origin allow-scripts"
        :src="`https://microdraw.pasteur.fr/data?source=${histology.url}`"
        width="1280"
        height="600"
        class="patient__histology"
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
    histologyItem() {
      const data = this.patient.data
      return data.filter((item) => {
        return item.type === 'Histology'
      })
    },
  },
}
</script>

<style>
.histology__toc {
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
.histology__content + .histology__content {
  margin-top: 8rem;
}
.patient__histology {
  min-height: 60rem;
}
.histology__title {
  margin-bottom: 2rem;
}
</style>
