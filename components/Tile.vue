<template>
  <div>
    <v-card>
      <v-img :src="image"></v-img>
      <v-card-title>{{ name }}</v-card-title>
      <v-card-actions>
        <nuxt-link :to="`/${slug}`"
          ><v-btn color="primary" text>Demo</v-btn></nuxt-link
        >
      </v-card-actions>
    </v-card>
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
