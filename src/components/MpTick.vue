<template>
  <li>
    <a v-bind:href="route.url"
      target="_blank">
      {{route.name}}
    </a>
    {{route.rating}} -
    {{tick.style ? tick.style + ' -': ''}}
    {{tick.leadStyle ? tick.leadStyle + ' -': ''}}
    {{routeArea}} - {{routeRegion}} - {{routeTerritory}}
  </li>
</template>

<script>
export default {
  name: 'MpTick',
  props: ['tick', 'route'],
  computed: {
    routeArea: function () {
      return this.route.location[this.route.location.length - 1]
    },
    routeRegion: function () {
      return this.route.location[this.route.location.length - 2]
    },
    routeTerritory: function () {
      return this.route.location[0]
    },
  }
}
</script>
