<template>
  <section class="toc">
    <slot name="title" />
    <strong>Open below:</strong>
    <nav aria-label="Quick access">
      <ul class="toc__list" clean-list>
        <li v-for="item of items" :key="item.id">
          <iframe-button :item="item" :rootUrl="getRootUrl" />
        </li>
      </ul>
    </nav>
  </section>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      default: () => null,
      required: true,
    },
    itemType: {
      type: String,
      default: null,
      required: true,
    },
  },
  computed: {
    getRootUrl() {
      const type = this.itemType
      let url
      switch (type) {
        case 'MRI':
          url = 'https://brainbox.pasteur.fr/mri?url='
          break
        case 'histology':
          url = 'https://microdraw.pasteur.fr/data?source='
          break
        default:
          url = 'http://localhost:3000'
          break
      }
      return url
    },
  },
}
</script>

<style scoped>
.toc {
  margin: 4rem 0;
}
.toc__list {
  margin-top: 2rem;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(300px, 100%), 1fr));
  gap: 2rem;
}
.toc__list__item {
  margin: 0;
  padding: 2rem;
  display: block;
  width: 100%;
}
</style>
