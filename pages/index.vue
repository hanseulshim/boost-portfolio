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
          :path="project.path"
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
          :path="project.path"
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
          name: 'Cruise Ship Visualization Prototype',
          path: 'ship',
          image: `${process.env.baseUrl}/assets/ship.png`,
          description:
            'In this interface, users can log in and see real-time updates to bookings for each cruise, and sailing. In addition, data can be compared with the average bookings, or against peer groups of similar sailings. The pièce de résistance is a 3D rotating ship visualization showing individual staterooms and their booking status. Staff can now see clusters of unsold staterooms and manage pricing and deals across cabin categories, decks, and even target individual staterooms.',
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
          name: 'Golem Drill Site Dashboard',
          path: 'golem',
          image: `${process.env.baseUrl}/assets/golem.png`,
          description:
            'This interface produces real-time data on drill bits and their journey as they drill down a particular well. The goal is to observe wear & tear insights to optimize when to switch out drill bits, and by doing so maximize cost savings.',
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
          name: 'Radian AVM Report',
          path: 'home-report',
          image: `${process.env.baseUrl}/assets/home-report.png`,
          description:
            'Radian looked to produce an automated report that users could generate from selecting a single property. Beyond general info on the selected property, the report would also produce in depth insights, including comparative data based on comparable properties and offer prescriptive feedback.',
          projectTypes: [
            'data product ui/ux design & development',
            'data visualization & reporting',
          ],
          techStack: ['react', 'amCharts'],
        },
        {
          key: 4,
          name: 'Radian Market Report',
          path: 'home',
          image: `${process.env.baseUrl}/assets/home.png`,
          description:
            'This was an automated report that users could generate by selecting a single property. It would produce in-depth insights with a strong focus on comparative data based on comparable properties.',
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
