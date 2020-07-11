<template>
  <div class="projects-section">
    <h2>Projects</h2>
    <div class="projects-grid">
      <project v-for="project in projects"
        :key="project.id"
        :project="project">
      </project>
    </div>
  </div>
</template>

<script>
import Project from './Project.vue'
export default {
  components: {
    Project
  },
  name: 'Projects',
  data: function() {
    return {
      projects: []
    }
  },
  created () {
    fetch("projects.json")
      .then(response => response.json())
      .then(json => this.projects = json)
  }
}
</script>

<style scoped>
</style>
