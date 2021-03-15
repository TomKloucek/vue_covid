<template>
  <div id="app">
    <h1>Situace COVID-19 v ČR</h1>
    <Card v-bind:apiData="this.apiData"/>
    <chart-container/>
    <sign/>
  </div>
</template>

<script>
import Card from './components/Card'
import ChartContainer from './components/ChartContainer'
import Sign from './components/Sign'

export default {
  name: 'App',
  components: {
    Card,
    ChartContainer,
    Sign,
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
  font-family: 'Courier New', Courier, monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(173, 173, 173);
  margin-top: 30px;
}

* {
  margin: 0 auto;
}

body {
    background-color: #1a1919;
}

h2 {
  margin-top: 10px;
}

h1 {
  margin-top: 30px;
  font-family: 'Courier New', Courier, monospace;
}

</style>
