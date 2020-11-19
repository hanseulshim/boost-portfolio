<template>
  <div class="main-container">
    <div class="title-container">
      <div class="spacer" />
      <h2>Demo Portal</h2>
    </div>
    <div class="project-type-container">
      <span
        v-for="projectType in projectTypes"
        :key="projectType"
        class="project-type"
        :class="{ selected: selectedProjectType === projectType }"
        @click="selectType(projectType)"
      >
        {{ projectType }}
      </span>
    </div>
    <div class="tile-column">
      <div class="tile-container">
        <Tile
          v-for="project in filtedProjects.filter((v) => v.key % 2 !== 0)"
          :key="project.key"
          :name="project.name"
          :description="project.description"
          :image="project.image"
          :project-types="project.projectTypes"
          :tech-stack="project.techStack"
        />
      </div>
      <div class="tile-container">
        <Tile
          v-for="project in filtedProjects.filter((v) => v.key % 2 === 0)"
          :key="project.key"
          :name="project.name"
          :description="project.description"
          :image="project.image"
          :project-types="project.projectTypes"
          :tech-stack="project.techStack"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  middleware: 'auth',
  data() {
    return {
      projects: [
        {
          key: 1,
          name: 'ship',
          image: `${process.env.baseUrl}/assets/ship.png`,
          description: 'Ship description needed but this is what it is for now',
          projectTypes: [
            'data analytics solution',
            'data product development',
            'data product ui/ux design & development',
            'data visualization & reporting',
          ],
          techStack: ['react', 'node.js', 'graphQL', 'plotly'],
        },
        {
          key: 2,
          name: 'golem',
          image: `${process.env.baseUrl}/assets/golem.png`,
          description:
            'Golem description needed but this is what it is for now',
          projectTypes: [
            'data analytics solution',
            'data product development',
            'data product ui/ux design & development',
            'data visualization & reporting',
          ],
          techStack: ['vue', 'd3'],
        },
        {
          key: 3,
          name: 'home report',
          image: `${process.env.baseUrl}/assets/home-report.png`,
          description:
            'Home Report description needed but this is what it is for now',
          projectTypes: [
            'data product ui/ux design & development',
            'data visualization & reporting',
          ],
          techStack: ['react', 'amCharts'],
        },
        {
          key: 4,
          name: 'home',
          image: `${process.env.baseUrl}/assets/home.png`,
          description: 'Home description needed but this is what it is for now',
          projectTypes: [
            'data product ui/ux design & development',
            'data visualization & reporting',
          ],
          techStack: ['react', 'amCharts'],
        },
      ],
      selectedProjectType: 'all',
      projectTypes: [
        'all',
        'data analytics solution',
        'data product development',
        'data product ui/ux design & development',
        'data visualization & reporting',
      ],
    }
  },
  computed: {
    filtedProjects() {
      return this.projects.filter((project) => {
        if (this.selectedProjectType === 'all') {
          return true
        }
        return project.projectTypes.includes(this.selectedProjectType)
      })
    },
  },
  methods: {
    selectType(projectType) {
      this.selectedProjectType = projectType
    },
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
.main-container {
  padding: 0 6em;
  max-width: 1600px;
  margin: auto;

  .title-container {
    margin-bottom: 4em;
    .spacer {
      width: 140px;
      height: 4px;
      background: #ff9a0b;
      margin-bottom: 1em;
    }
  }
  .project-type-container {
    display: flex;
    justify-content: space-between;
    margin-bottom: 1em;

    .project-type {
      text-transform: uppercase;
      cursor: pointer;
      &:hover {
        color: #ff9a0b;
      }
      &.selected {
        color: #ff9a0b;
      }
    }

    @media (max-width: 1334px) {
      font-size: 0.8em;
    }
  }
  .tile-column {
    display: flex;
    justify-content: space-between;
    margin-bottom: 2em;
    box-sizing: border-box;

    .tile-container {
      width: 49%;
      display: flex;
      flex-direction: column;
    }
  }
}
</style>
