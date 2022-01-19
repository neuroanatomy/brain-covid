<template>
  <main id="main-content">
    <links-list :items="mriItems" itemType="MRI">
      <template #title>
        <h1>Magnetic resonance imaging data of patient {{ patient.id }}</h1>
      </template>
    </links-list>
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
