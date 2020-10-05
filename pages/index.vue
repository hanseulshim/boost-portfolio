<template>
  <div class="container">
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
          image: 'https://s3.amazonaws.com/demo.boostlabs/assets/ship.png',
        },
        {
          key: 2,
          slug: 'golem',
          name: 'Golem',
          image: 'https://s3.amazonaws.com/demo.boostlabs/assets/golem.png',
        },
        {
          key: 3,
          slug: 'home',
          name: 'Home',
          image: 'https://s3.amazonaws.com/demo.boostlabs/assets/home.png',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.container {
  padding: 3em;
  display: grid;
  grid-template-columns: auto auto;
  grid-gap: 2em;
}
</style>
