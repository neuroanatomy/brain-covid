<template>
  <div>
    <iframe
      sandbox="allow-same-origin allow-scripts"
      :src="url"
      class="data-iframe"
      width="1310"
      height="800"
      frameborder="0"
    ></iframe>
  </div>
</template>

<script>
export default {
  props: {
    url: {
      type: String,
      default: null,
    },
  },
}
</script>
