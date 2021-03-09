<script>
import { Bar } from 'vue-chartjs'

export default {
  extends: Bar,
  data: () => ({
    chartdata: {
      labels: ['Infected', 'Recovered','Dead','Vaccinated'],
      datasets: [
        {
          label: 'Number of people',
          backgroundColor: ['#53db56','#635bba','#c44037','#a553cf'],
          data: [this.apiData.aktivni_pripady, this.apiData.vyleceni, this.apiData.umrti, this.apiData.vykazana_ockovani_celkem/2]
        }
      ]
    },
    props: ['apiData'],
    options: {
      responsive: true,
      maintainAspectRatio: false
    }
  }),
  mounted () {
    this.renderChart(this.chartdata, this.options)
  }
}
</script>

<style scoped>
</style>
