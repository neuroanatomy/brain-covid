<template>
  <source :srcset="cSizes.srcset" :sizes="cSizes.sizes" :type="type" />
</template>

<script>
export default {
  props: {
    src: { type: String },
    sizes: { type: String },
    type: { type: String },
  },
  computed: {
    cSizes() {
      return this.$img.getSizes(this.src, {
        sizes: this.sizes,
      })
    },
  },
}
</script>
