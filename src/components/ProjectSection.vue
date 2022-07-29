<template>
  <div class="projects-section">
    <h2 class="title">Projects</h2>
    <transition name="fade">
      <div class="projects-grid" v-show="showProjects">
        <ProjectCard v-for="project in projects"
          @project-img-loaded="onProjectImgLoaded"
          :key="project.id"
          :project="project">
        </ProjectCard>
      </div>
    </transition>
  </div>
</template>

<script>
import ProjectCard from './ProjectCard.vue'
export default {
  components: {
    ProjectCard
},
  name: 'ProjectSection',
  data: function() {
    return {
      projects: [],
      showProjects: false,
      imgsToLoad: new Set()
    }
  },
  created () {
    fetch("projects.json")
      .then(response => response.json())
      .then(json => {
        this.projects = json
        // for project.img in projects
        json.reduce(function(acc, currentProject) {
          return acc.add(currentProject.img)
        }, this.imgsToLoad)
      })
  },
  methods: {
    onProjectImgLoaded: function(imgName) {
      this.imgsToLoad.delete(imgName);
      this.showProjects = (this.imgsToLoad.size == 0)
    }
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
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}

/* project list fade in */
.fade-enter-active {
  transition: opacity 0.8s ease-in-out;
}

.fade-enter-to {
  opacity: 1;
}

.fade-enter {
  opacity: 0;
}
</style>
