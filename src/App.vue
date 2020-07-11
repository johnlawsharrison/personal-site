<template>
  <div id="app">
    <div class="banner">
      <h1>John Laws Harrison</h1>
      <h2>full-stack engineer</h2>
      <div class="link-bar">
        <a href="mailto:johnlawsharrison@gmail.com"><i class="fas fa-envelope"></i></a>
        <a href="https://github.com/johnlawsharrison" target="_blank"><i class="fab fa-github"></i></a>
        <a href="https://linkedin.com/in/johnlawsharrison" target="_blank"><i class="fab fa-linkedin"></i></a>
      </div>
    </div>
    <Projects/>
    <TickList v-if="false"/>
  </div>
</template>

<script>
import Projects from './components/Projects.vue'
import TickList from './components/TickList.vue'

export default {
  name: 'App',
  components: {
    Projects,
    TickList
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
  transition: color 0.5s ease;
}

a:hover {
  color: #B48;
}

/* FontAwesome icon globals */
.fas, .fab {
  color: #B48;
}

/* banner */

.banner {
  padding: 20vh 0px 0px 0px;
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
  transition: opacity 1.0s ease;
}

.link-bar a:hover {
  opacity: 0.5;
}
</style>
