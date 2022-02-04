<template>
  <nuxt-link
    class="card"
    :to="{ name: `${type}-slug`, params: { slug: item.id } }"
  >
    <div v-if="item.data" class="card__thumbnail">
      <nuxt-picture
        :src="`/${type}/${item.id}/thumbnail.jpg`"
        sizes="sm:100vw lg:100px"
        width="100"
        height="100"
        alt=""
      />
    </div>
    <div class="card__content">
      <h3>Patient {{ item.id }}</h3>
      <ul class="card__meta" clean-list>
        <li><strong>Age: </strong>{{ item.age }}</li>
        <li><strong>Gender: </strong>{{ item.gender }}</li>
      </ul>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
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
.card {
  margin: 0;
  display: flex;
  flex-flow: row nowrap;
  overflow: hidden;
  text-decoration: none;
  border-radius: 4px;
  outline: solid 1px var(--accent);
  outline-offset: 0;
  transition: outline-offset 0.2s ease;
}
.card:hover {
  outline-offset: 5px;
}
.card:focus-visible {
  outline: solid 3px var(--contrast);
  text-decoration: none;
}
.card__thumbnail {
  position: relative;
}
.card__thumbnail ::v-deep picture,
.card__thumbnail ::v-deep img {
  position: relative;
  height: 100%;
}
.card__thumbnail ::v-deep img {
  object-fit: cover;
}
.card__content {
  padding: 2rem 2rem 2.4rem;
}
.card__content > * + * {
  margin-top: 1.2rem;
  margin-bottom: 0;
}
</style>
