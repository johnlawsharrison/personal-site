<template>
  <div class="tile">
    <a :href="project.websiteUrl" target="_blank">
      <figure>
        <template v-if="project.img.split('.').pop() == 'mp4'">
          <video
            v-on:loadeddata="onImgLoaded"
            autoplay
            loop
            muted
            playsinline
            :alt="project.title">
            <source :src="require(`@/assets/${project.img}`)" type="video/mp4">
          </video>
        </template>
        <img v-else class="project-img" v-on:load="onImgLoaded" :src="require(`@/assets/${project.img}`)" :alt="project.title">
        <figcaption>
          <h3>
              {{ project.title }}
          </h3>
        </figcaption>
      </figure>
    </a>
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
  props: ['project'],
  methods: {
    onImgLoaded() {
      this.$emit('project-img-loaded', this.project.img);
    }
  }
}
</script>

<style scoped>
.tile {
  background: linear-gradient(#b48, #991149);
  color: white;
  /* background-color: #B48; */
}

figure {
  max-height: 220px;
  width: 100%;
  margin: 0;
  overflow: hidden;
  position: relative;
  color: white;
  transition: color 0.3s ease;
}

figure > img, figure > video {
  width: 100%;
  min-height: 220px;
}

figure > video {
  object-fit: fill;
}

figure > figcaption {
  color: inherit;
  background-color: rgba(0, 0, 0, 0.6);
  position: absolute;
  bottom: 0;
  width: 100%;
}

figure figcaption h3 {
  padding: 0.5rem;
}

p {
  padding: 1rem;
}

figure:hover {
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
  background-color:rgba(0, 0, 0, 0.6);
  /* color: white; */
  border-radius: 0.5rem;
  padding: 0.5rem;
}

</style>
