<template>
  <div class="member">
    <nuxt-picture
      v-if="member.photo"
      :src="member.photo"
      width="80"
      height="80"
      loading="lazy"
      class="member__photo"
    />
    <div class="member__info">
      <h3 class="member__name">{{ member.name }}</h3>
      <p class="member__role">{{ member.role }}</p>
      <p class="member__job">{{ member.job }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    member: {
      type: Object,
      default: () => null,
      required: true,
    },
  },
}
</script>

<style scoped>
.member {
  padding: 2rem 1.6rem;
  height: 100%;
  display: flex;
  flex-flow: row wrap;
  align-items: flex-start;
  align-content: center;
  gap: calc(1rem + 1vw);
  font-size: clamp(1.4rem, 1.3354rem + 0.202vw, 1.6rem);
  text-align: left;
  border: 1px solid var(--accent);
  border-radius: 1rem;
}
.member * {
  margin: 0;
}

.member__info {
  flex-basis: 0;
  flex-grow: 999;
  min-width: 60%;
}
.member__photo {
  flex-basis: 80px;
  flex-grow: 1;
}

.member__info > * + * {
  margin-top: 0.6rem;
}
.member__photo ::v-deep img {
  border-radius: 50%;
}
</style>
