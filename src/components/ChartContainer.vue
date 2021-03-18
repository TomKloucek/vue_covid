<template>
  <div class="chart_container">
    <pie-chart
      v-if="loaded"
      :chartdata="chartdata"
      :options="options" />
  </div>
</template>

<script>
import PieChart from './Chart.vue'
import axios from 'axios'

export default {
  name: 'PieChartContainer',
  components: { PieChart },
  data: () => ({
    loaded: false,
    chartdata: null,
    apiData: null
  }),
  async mounted () {
    this.loaded = false
    try {
      const data  = await axios.get('https://onemocneni-aktualne.mzcr.cz/api/v2/covid-19/zakladni-prehled.json')
      const datasets = {
      labels: ['Infected', 'Recovered','Dead','Vaccinated'],
      datasets: [
        {
          label: `Aktualni k datu: ${data.data.data[0].datum}`,
          backgroundColor: ['#53db56','#635bba','#c44037','#a553cf'],
          data: [data.data.data[0].aktivni_pripady,data.data.data[0].vyleceni,data.data.data[0].umrti,Math.round(data.data.data[0].vykazana_ockovani_celkem/2)]
        }
      ]
    }
      console.log(data.data.data[0])
      this.chartdata = datasets
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<style >
.chart_container{
  width: 350px;
}
</style>