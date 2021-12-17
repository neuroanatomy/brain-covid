<template>
  <main id="main-content">
    <section id="cases" class="cases">
      <h1>All cases</h1>
      <card-list :list="patients" :type="type" />
    </section>
  </main>
</template>

<script>
export default {
  name: 'PatientsPage',

  async asyncData({ $content, error }) {
    const patients = await $content('patients')
      .only(['id', 'age', 'gender'])
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
      type: 'patients',
    }
  },
}
</script>
