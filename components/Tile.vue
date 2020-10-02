<template>
  <div class="tile">
    <img class="image" :src="image" />
    <nuxt-link class="title" :to="`/${slug}`">{{ name }}</nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    slug: {
      type: String,
      default: 'N/A',
    },
    name: {
      type: String,
      default: 'N/A',
    },
    image: {
      type: String,
      default: 'N/A',
    },
  },
}
</script>

<style lang="scss" scoped>
.tile {
  width: 100%;
  display: flex;
  flex-direction: column;

  .title {
    width: 100%;
    font-size: 1.5em;
    text-align: center;
    background: #f0efed;
    padding: 0.25em 0;
    color: #161616;
    text-decoration: none;
  }

  .image {
    width: 100%;
  }
}
</style>
