<template>
  <nuxt-link :to="`/${path}`"
    ><div class="tile" @mouseover="hover = true" @mouseleave="hover = false">
      <img :src="image" />
      <div v-if="hover" class="project-tile">
        <h2 class="title">{{ name }}</h2>
        <div class="description">{{ description }}</div>
        <div class="tag-container">
          <div class="tag type">{{ projectTypes.join(', ') }}</div>
          <div class="tag tech">{{ techStack.join(', ') }}</div>
        </div>
      </div>
    </div></nuxt-link
  >
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: 'N/A',
    },
    path: {
      type: String,
      default: 'N/A',
    },
    description: {
      type: String,
      default: 'N/A',
    },
    image: {
      type: String,
      default: 'N/A',
    },
    projectTypes: {
      type: Array,
      default: () => [],
    },
    techStack: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      hover: false,
    }
  },
}
</script>

<style lang="scss" scoped>
.tile {
  display: inline-block;
  width: 100%;
  margin-top: 1em;
  position: relative;

  &:hover {
    cursor: pointer;
  }

  img {
    width: 100%;
  }

  .project-tile {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    background: #000;
    opacity: 0.75;
    padding: 2em;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    .title {
      text-transform: capitalize;
    }

    .description {
      margin: 1em 0;
      flex: 1;
    }
    .tag-container {
      display: flex;
      justify-content: space-between;
      flex: 1;
      .type {
        text-transform: uppercase;
      }
      .tech {
        text-transform: capitalize;
      }
      .tag {
        width: 48%;
      }
    }
  }
}
</style>
