<template>
  <div class="tile-container">
    <Tile
      v-for="page in pages"
      :key="page.key"
      :slug="page.slug"
      :name="page.name"
      :image="page.image"
    />
  </div>
</template>

<script>
export default {
  middleware: 'auth',
  data() {
    return {
      pages: [
        {
          key: 1,
          slug: 'ship',
          name: 'Ship',
          image: `${process.env.baseUrl}/assets/ship.png`,
        },
        {
          key: 2,
          slug: 'golem',
          name: 'Golem',
          image: `${process.env.baseUrl}/assets/golem.png`,
        },
        {
          key: 3,
          slug: 'home',
          name: 'Home',
          image: `${process.env.baseUrl}/assets/home.png`,
        },
      ],
    }
  },
  head() {
    return {
      title: 'Boost Labs Demo',
      meta: [
        {
          hid: 'demo home page',
          name: 'demo home page',
          content: 'Boost Labs demo home page',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.tile-container {
  padding: 3em 6em;
  display: grid;
  grid-template-columns: 50% 50%;
  grid-gap: 2em;
  max-width: 1600px;
  margin: auto;
}
</style>
