<template>
  <main id="main-content">
    <links-list :items="mriItems" itemType="MRI">
      <template #title>
        <h1>Magnetic resonance imaging data of patient {{ patient.id }}</h1>
      </template>
    </links-list>
    <iframe-item v-if="currentUrl" :url="currentUrl" />
    <p v-else>Open an interactive MRI view with one of the above buttons.</p>
  </main>
</template>

<script>
export default {
  // fetch the patient's data based on the slug parameter
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
      // start without an iframe for performance
      currentUrl: null,
    }
  },
  computed: {
    mriItems() {
      // only return the MRI items from the patient's data
      const data = this.patient.data
      return data.filter((item) => {
        return item.type === 'MRI'
      })
    },
  },
  created() {
    // listen on the 'button-click' envent and update the iframe's url accordingly
    this.$nuxt.$on('button-click', (url) => {
      this.currentUrl = url
    })
  },
}
</script>
