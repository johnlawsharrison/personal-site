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
      <a href="https://www.mountainproject.com/user/200538569/john-laws" target="_blank">
        mountainproject.com
      </a>
    </h4>
    <ul>
      <Tick v-for="tick in ticks"
        :key="tick.id"
        :tick="tick"
        :route="routeData[tick.routeId]"/>
    </ul>
  </div>
</template>

<script>
import Tick from './Tick.vue'

export default {
  components: {
    Tick
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
    // TODO: LOAD API KEY USING dotenv and set these urls as constants somewhere
    const ticksUrl = `https://www.mountainproject.com/data/get-ticks?email=johnlawsharrison@gmail.com&key=${process.env.VUE_APP_MP_API_KEY}`
    const routesUrl = `https://www.mountainproject.com/data/get-routes?key=${process.env.VUE_APP_MP_API_KEY}&routeIds=`
    fetch(ticksUrl)
      .then(response => response.json())
      .then(json => json.ticks.slice(0, 5))
      .then(ticks => {
        var routeIds = ticks.map(a => a.routeId).join(',');
        this.ticks = ticks;
        return fetch(routesUrl + routeIds)
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
