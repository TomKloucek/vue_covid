<template>
  <div id="app">
    <h2>Up to date: {{this.apiData.datum}}</h2>
    <Card v-bind:apiData="this.apiData"/>
    <Chart-container v-bind:apiData="this.apiData"/>
  </div>
</template>

<script>
import Card from './components/Card'
import ChartContainer from './components/ChartContainer'

export default {
  name: 'App',
  components: {
    Card,
    ChartContainer,
  },
  data() {
    return {
        apiData: null
    }
  },
  created() {
    fetch(
      'https://onemocneni-aktualne.mzcr.cz/api/v2/covid-19/zakladni-prehled.json')
      .then((response) => response.json())
      .then((data) => this.apiData = data.data[0]); 
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

* {
  margin: 0 auto;
}

h2 {
  margin-top: 5%;
}
</style>
