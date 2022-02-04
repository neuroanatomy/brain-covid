<template>
  <button :href="item.url" class="button toc__list__item" @click="updateUrl">
    <span v-if="item.sequence">{{ item.sequence }} - </span>{{ item.comments }}
  </button>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      default: () => null,
      required: true,
    },
    rootUrl: {
      type: String,
      default: null,
      required: true,
    },
  },
  computed: {
    getFullUrl() {
      // create the full iframe's url with the service's url and the item's url
      return this.rootUrl + this.item.url
    },
  },
  methods: {
    updateUrl() {
      // method triggered by click sending the event too the root component
      this.$nuxt.$emit('button-click', this.getFullUrl)
    },
  },
}
</script>

<style scoped></style>
