<template>
  <li>
    <a v-bind:href="route.url"
      target="_blank">
      {{route.name}}
    </a>
    {{route.rating}} - {{tick.style}} - {{tick.leadStyle}} - {{routeArea}} - {{routeTerritory}}
  </li>
</template>

<script>
export default {
  name: 'Tick',
  props: ['tick', 'route'],
  computed: {
    routeArea: function () {
      return this.route.location[this.route.location.length - 1]
    },
    routeTerritory: function () {
      return this.route.location[0]
    }
  }
}
</script>
