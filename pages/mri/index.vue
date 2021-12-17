<template>
  <main id="main-content">
    <section id="cases" class="cases">
      <h1>MRIs of patients</h1>
      <card-list :list="patients" :type="type" />
    </section>
  </main>
</template>

<script>
export default {
  name: 'MRIPage',

  async asyncData({ $content, error }) {
    const patients = await $content('patients')
      .only(['id', 'data'])
      .sortBy('createdAt', 'asc')
      .fetch()
      .catch((err) => {
        error({ statusCode: 404, message: 'Page not found' })
        console.log(err)
      })

    return {
      patients,
    }
  },
  data() {
    return {
      type: 'mri',
    }
  },
}
</script>

<style scoped></style>
