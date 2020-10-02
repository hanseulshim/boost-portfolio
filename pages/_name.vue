<template>
  <div id="container">
    <img
      v-if="!iframeLoaded"
      id="loader"
      src="https://s3.amazonaws.com/demo.boostlabs/assets/loader.gif"
    />
    <iframe
      v-show="iframeLoaded"
      width="100%"
      height="100%"
      :src="slug"
      @load="iframeLoad"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      iframeLoaded: false,
    }
  },
  computed: {
    slug() {
      return `https://s3.amazonaws.com/demo.boostlabs/${this.$route.params.name}/index.html`
    },
  },
  methods: {
    iframeLoad(e) {
      this.iframeLoaded = true
    },
  },
}
</script>

<style lang="scss">
#container {
  height: 100vh;

  #loader {
    width: 100%;
  }

  iframe {
    border: none;
  }
}
</style>
