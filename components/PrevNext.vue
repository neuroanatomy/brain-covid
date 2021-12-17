<template>
  <nav v-if="prev || next">
    <h2>Other patients</h2>
    <div class="prevNext">
      <nuxt-link
        v-if="prev"
        :to="{ name: `${routeName}-slug`, params: { slug: prev.slug } }"
        class="prevNext__prev"
        clean-link
      >
        <p class="prevNext__label">
          Previous:
          <span class="prevNext__title">Patient {{ prev.id }}</span>
        </p>
      </nuxt-link>
      <span v-else>&nbsp;</span>
      <nuxt-link
        v-if="next"
        :to="{ name: `${routeName}-slug`, params: { slug: next.slug } }"
        class="prevNext__next"
        clean-link
      >
        <p class="prevNext__label">
          Next:
          <span class="prevNext__title">Patient {{ next.id }}</span>
        </p>
      </nuxt-link>
      <span v-else>&nbsp;</span>
    </div>
  </nav>
</template>

<script>
export default {
  props: {
    prev: {
      type: Object,
      default: () => null,
    },
    next: {
      type: Object,
      default: () => null,
    },
    routeName: {
      type: String,
      default: '',
    },
  },
}
</script>

<style scoped>
nav {
  margin: 6rem 0 4rem;
  padding: 2rem 1rem;
  border-top: 1rem dotted var(--accent);
}
h2 {
  margin: 0 0 20px;
  padding-bottom: 4px;
  display: block;
  color: var(--brique);
  border-bottom: 6px dotted var(--lightBlue);
}
.prevNext {
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  align-items: flex-start;
}
.prevNext__prev,
.prevNext__next {
  position: relative;
  border: none;
  flex: 0 0 48%;
}
.prevNext__prev {
  padding-left: 30px;
}
.prevNext__next {
  padding-right: 30px;
  text-align: right;
}

.prevNext__prev::before,
.prevNext__next::before {
  content: '→';
  position: absolute;
  top: 50%;
  width: 20px;
  transition: transform 0.3s ease;
}
.prevNext__prev::before {
  left: 0;
  transform: translate(0, -50%) rotate(180deg);
}
.prevNext__next::before {
  right: 0;
  transform: translate(0, -50%);
}
.prevNext__prev:hover::before,
.prevNext__prev:focus::before {
  transform: translate(-10px, -50%) rotate(180deg);
}
.prevNext__next:hover::before,
.prevNext__next:focus::before {
  transform: translate(10px, -50%);
}
.prevNext__label {
  margin: 0;
}
.prevNext__title {
  display: block;
  font-size: 1.4rem;
  line-height: 1;
  font-weight: 500;
  color: var(--blue);
}
</style>
