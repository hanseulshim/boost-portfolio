<template>
  <div id="container">
    <div v-if="!iframeLoaded" class="loader-container">
      <div id="loader">
        <div id="shadow"></div>
        <div id="box"></div>
      </div>
    </div>
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
  middleware: 'auth',
  data() {
    return {
      iframeLoaded: false,
    }
  },
  computed: {
    slug() {
      return `${process.env.baseUrl}/${this.$route.params.name}/index.html`
    },
  },
  methods: {
    iframeLoad() {
      this.iframeLoaded = true
    },
  },
  head() {
    return {
      title: `Boost Labs Demo - ${this.$route.params.name}`,
      meta: [
        {
          hid: `demo ${this.$route.params.name} page`,
          name: `demo ${this.$route.params.name} page`,
          content: `Boost Labs demo ${this.$route.params.name} page`,
        },
      ],
    }
  },
}
</script>

<style lang="scss">
#container {
  height: 100vh;

  iframe {
    border: none;
  }
  .loader-container {
    position: relative;
    width: 300px;
    height: 200px;
    margin: auto;
  }

  #loader {
    animation: loader 5s linear infinite;

    position: absolute;
    top: calc(50% - 20px);
    left: calc(50% - 20px);
  }
  @keyframes loader {
    0% {
      left: -100px;
    }
    100% {
      left: 110%;
    }
  }
  #box {
    width: 50px;
    height: 50px;
    background: #fff;
    animation: animate 0.5s linear infinite;
    position: absolute;
    top: 0;
    left: 0;
    border-radius: 3px;
  }
  @keyframes animate {
    17% {
      border-bottom-right-radius: 3px;
    }
    25% {
      transform: translateY(9px) rotate(22.5deg);
    }
    50% {
      transform: translateY(18px) scale(1, 0.9) rotate(45deg);
      border-bottom-right-radius: 40px;
    }
    75% {
      transform: translateY(9px) rotate(67.5deg);
    }
    100% {
      transform: translateY(0) rotate(90deg);
    }
  }
  #shadow {
    width: 50px;
    height: 5px;
    background: #000;
    opacity: 0.1;
    position: absolute;
    top: 59px;
    left: 0;
    border-radius: 50%;
    animation: shadow 0.5s linear infinite;
  }
  @keyframes shadow {
    50% {
      transform: scale(1.2, 1);
    }
  }
}
</style>
