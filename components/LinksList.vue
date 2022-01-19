<template>
  <section class="toc">
    <slot name="title" />
    <strong>Open in new tab:</strong>
    <nav aria-label="Quick access">
      <ul class="toc__list" clean-list>
        <li v-for="item of items" :key="item.id">
          <a
            :href="getUrlByType + item.url"
            rel="noreferer noopener"
            target="_blank"
            class="button toc__list__item"
            :title="`Open ${item.sequence} - ${item.comments} in new tab`"
            ><span v-if="item.sequence">{{ item.sequence }} - </span
            >{{ item.comments }}</a
          >
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
    getUrlByType() {
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
  /* padding: 2rem; */
  /* border-radius: 8px; */
  /* background-color: var(--accent-dark); */
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
}
</style>
