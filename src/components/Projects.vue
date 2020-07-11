<template>
  <div class="projects-section">
    <h2 class="title">Projects</h2>
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
.projects-section {
  padding: 2rem;
}

.title {
  margin: 0 0 1rem 0;
}

/* Grid layout */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 1rem;
}

</style>
