<template>
  <main id="main-content">
    <section id="cases" class="intro">
      <h1>Histological data.</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Laudantium quo
        voluptates saepe ad delectus! Ut nulla debitis ducimus sint illo! Illum,
        possimus? Id laudantium accusantium consequuntur officiis possimus?
        Maiores, temporibus?
      </p>
      <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Deserunt
        sapiente delectus adipisci nulla error facilis animi provident fugiat
        architecto voluptatem amet quaerat, nobis debitis quisquam quidem eius
        ex harum quae.
      </p>
    </section>
    <section>
      <h2>Patients list</h2>
      <card-list :list="patients" :type="type" />
    </section>
  </main>
</template>

<script>
export default {
  name: 'HistologyPage',

  async asyncData({ $content, error }) {
    const patients = await $content('patients')
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
      type: 'histology',
    }
  },
}
</script>

<style scoped></style>
