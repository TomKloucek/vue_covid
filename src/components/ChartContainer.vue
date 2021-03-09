<template>
  <div class="container">
    <bar-chart
      v-if="loaded"
      :chartdata="chartdata"
      :options="options" v-bind:apiData="this.apiData"/>
  </div>
</template>

<script>
import BarChart from './Chart.vue'

export default {
  name: 'BarChartContainer',
  components: { BarChart },
  data: () => ({
    loaded: false,
    chartdata: null
  }),
  props: ['apiData'],
  async mounted () {
    this.loaded = false
    try {
      this.chartdata = 5
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>