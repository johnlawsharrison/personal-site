<template>
  <div id="app">
    <div class="banner">
      <h1>John Laws Harrison</h1>
      <h2>software engineer</h2>
      <div class="link-bar">
        <a href="mailto:johnlawsharrison@gmail.com"><i class="fas fa-envelope"></i></a>
        <a href="https://github.com/johnlawsharrison" target="_blank"><i class="fab fa-github"></i></a>
        <a href="https://linkedin.com/in/johnlawsharrison" target="_blank"><i class="fab fa-linkedin"></i></a>
      </div>
      <a class="button" :href="`${publicPath}JohnLawsResume.pdf`" target="_blank">
          Resume
      </a>
    </div>
    <ProjectSection/>
    <MpTickList/>
  </div>
</template>

<script>
import ProjectSection from './components/ProjectSection.vue'
import MpTickList from './components/MpTickList.vue'

export default {
  name: 'App',
  components: {
    ProjectSection,
    MpTickList
},
  data () {
  return {
    publicPath: process.env.BASE_URL
  }
}
}
</script>

<style>
/* General styles */
html, body{
  height: 100%;
}

body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Nunito, 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
}

h1, h2 {
  margin: 0;
}

a {
  color: inherit;
  text-decoration: none;
  transition: color 0.4s ease;
}

a:hover {
  color: #B48;
}

/* FA icon/button globals */
.fas, .fab, a.button {
  color: #B48;
  transition: opacity 0.4s ease;
}

a > .fas:hover, a > .fab:hover, a.button:hover {
  opacity: 0.5;
}

/* banner */

.banner {
  padding: 10vh 0px 0px 0px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.banner h1, h2 {
  font-family: 'Nova Slim';
  font-weight: 400;
}

.link-bar a {
  opacity: 1;
  font-size: 48px;
  margin-right: 8px;
}

a.button {
  background-color: #B48;
  color:white;
  padding: 0.5rem;
}
</style>
