<template>
  <div class="tile">
    <img class="project-img" src="@/assets/placeholder.png" :alt="project.title">
    <div class="tile-content">
      <h3>
        <a :href="project.websiteUrl" target="_blank">
          {{ project.title }}
        </a>
      </h3>
      <ul class="project-tags">
        <li v-for="tag in project.tags"
          :key="tag">
          {{ tag }}
        </li>
      </ul>
      <p>{{ project.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Project',
  props: ['project']
}
</script>

<style scoped>
.tile {
  display: flex;
  flex-direction: row;
  padding: 1rem;
  background-color: #FA5;
}

.project-img {
  height: 150px;
  margin-right: 1rem;
}

a:hover {
  color: white;
}

.project-tags {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  padding: 0;
  list-style-type: none;
  /* TODO: wrap tags */
}

.project-tags li {
  margin-right: 1rem;
}
</style>
