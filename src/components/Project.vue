<template>
  <div class="tile">
    <figure>
      <img class="project-img" :src="require(`@/assets/${project.img}`)" :alt="project.title">
      <figcaption>
        <h3>
          <a :href="project.websiteUrl" target="_blank">
            {{ project.title }}
          </a>
        </h3>
      </figcaption>
    </figure>
    <ul class="project-tags">
      <li v-for="tag in project.tags"
        :key="tag">
        {{ tag }}
      </li>
    </ul>
    <p>{{ project.description }}</p>
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
  background-color: #B48;
}

.tile > figure {
  max-height: 220px;
  width: 100%;
  margin: 0;
  overflow: hidden;
  position: relative;
}

.tile > figure > img {
  width: 100%;
}

.tile > figure > figcaption {
  color: white;
  background-color: rgba(0, 0, 0, 0.4);
  position: absolute;
  bottom: 0;
  width: 100%
}

.tile > figure > figcaption > h3 {
  padding: 0.5rem;
}

p {
  padding: 1rem;
}

a:hover {
  color: #B48;
}

.project-tags {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  padding: 0 0.5rem;
  list-style-type: none;
}

.project-tags li {
  margin: 0.1rem;
  background-color: black;
  color: white;
  border-radius: 0.5rem;
  padding: 0.5rem;
}
</style>
