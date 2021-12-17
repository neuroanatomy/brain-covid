<template>
  <main id="main-content">
    <article class="editorial">
      <h1>Patient {{ patient.id }}</h1>
      <p>Age: {{ patient.age }}</p>
      <p>Gender: {{ patient.gender }}</p>
      <div class="patient__links">
        <nuxt-link class="button" :to="`/mri/${patient.id}`"
          >See patient's MRIs</nuxt-link
        >
        <nuxt-link class="button" :to="`/histology/${patient.id}`"
          >See patient's histology</nuxt-link
        >
      </div>
    </article>
    <nav class="prevNext__nav">
      <LazyPrevNext :prev="prev" :next="next" :route-name="'patients'" />
    </nav>
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
    const [prev, next] = await $content('patients')
      .only(['id'])
      .sortBy('createdAt', 'asc')
      .surround(slug)
      .fetch()

    return { patient, prev, next }
  },
  head() {
    return {
      name: 'Patient: ' + this.patient.id,
    }
  },
}
</script>

<style>
.patient__links {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
</style>
