<template>
  <div class="mountain-project-section" v-if="showTicks">
    <a href="https://www.mountainproject.com/user/200538569/john-laws" target="_blank">
      <i class="fas fa-mountain"></i>
    </a>
    <h2>
        Most recent routes climbed
    </h2>
    <h4>
      data from
      <a href="https://www.mountainproject.com/data" target="_blank">
        mountainproject.com
      </a>
    </h4>
    <ul>
      <MpTick v-for="tick in ticks"
        :key="tick.id"
        :tick="tick"
        :route="routeData[tick.routeId]"/>
    </ul>
  </div>
</template>

<script>
import MpTick from './MpTick.vue'

export default {
  components: {
    MpTick
},
  name: 'TickList',
  data: function() {
    return {
      ticks: [],
      routeData: {},
      showTicks: false
    }
  },
  created () {
    this.TICKS_URL = `https://us-west2-coastal-sanctum-290521.cloudfunctions.net/mountain-project-proxy`
    this.ROUTES_URL = `https://us-west2-coastal-sanctum-290521.cloudfunctions.net/mountain-project-proxy?routeIds=`
    fetch(this.TICKS_URL)
      .then(response => response.json())
      .then(json => json.ticks.slice(0, 10))
      .then(ticks => {
        var routeIds = ticks.map(a => a.routeId).join(',');
        this.ticks = ticks;
        return fetch(this.ROUTES_URL + routeIds)
      })
      .then(response => response.json())
      .then(json => {
        this.routeData = json.routes.reduce((obj, item) => {
          obj[item['id']] = item
          return obj
        }, {})
        // all data for routes is loaded, display
        this.showTicks = true
      })
  }
}
</script>
<style scoped>
.mountain-project-section {
  /* TODO: refactor "sections" into one css rule */
  padding: 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h2 {
  text-align: center;
}

h4 {
  margin: 0;
}

.fa-mountain {
  font-size: 48px;
  margin-bottom: 0.5rem;
}

</style>
