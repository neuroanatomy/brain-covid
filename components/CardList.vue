<template>
  <ul class="cases__list" clean-list>
    <li v-for="patient of list" :key="patient.id">
      <basic-card :item="patient" :type="type" />
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    list: {
      type: Array,
      default: () => null,
    },
    type: {
      type: String,
      default: 'patients',
    },
  },
}
</script>

<style scoped>
.cases__list {
  margin: 2rem 0;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(340px, 100%), 1fr));
  gap: 3rem;
}
</style>
