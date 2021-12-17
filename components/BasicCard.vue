<template>
  <div class="card">
    <div v-if="item.data" class="card__thumbnail">
      <nuxt-picture
        :src="`/${type}/${item.id}/thumbnail.jpg`"
        sizes="sm:100vw lg:311px"
        width="311"
        height="160"
        alt=""
      />
    </div>
    <div class="card__content">
      <h3>
        <nuxt-link
          class="nice-link"
          :to="{ name: `${type}-slug`, params: { slug: item.id } }"
        >
          Patient {{ item.id }}
        </nuxt-link>
      </h3>
      <p class="card__meta">age: {{ item.age }}, gender: {{ item.gender }}</p>
    </div>
  </div>
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
  flex-direction: column;
  overflow: hidden;
  border-radius: 4px;
  border: solid 1px var(--accent);
}
.card > :last-child {
  margin-top: auto;
}
.card__thumbnail img {
  display: block;
}
.card__content {
  padding: 2rem 2rem 2.4rem;
}
.card__content > * + * {
  margin-top: 1.2rem;
  margin-bottom: 0;
}
</style>
