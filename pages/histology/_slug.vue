<template>
  <main id="main-content">
    <links-list :items="histologyItem" itemType="histology">
      <template #title>
        <h1>Histological data of patient {{ patient.id }}</h1>
      </template>
    </links-list>
    <iframe-item v-if="currentUrl" :url="currentUrl" />
    <p v-else>
      Open an interactive histological view with one of the above buttons.
    </p>
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
  data() {
    return {
      currentUrl: null,
    }
  },
  computed: {
    histologyItem() {
      const data = this.patient.data
      return data.filter((item) => {
        return item.type === 'Histology'
      })
    },
  },
  created() {
    this.$nuxt.$on('button-click', (url) => {
      this.currentUrl = url
    })
  },
}
</script>
