<template>
  <div v-bind:class="[theme, (theme === true) ? 'dark' : 'bright']" id="app">
    <h1>Situace COVID-19 v ČR</h1>
    <Card v-bind:apiData="this.apiData"/>
    <chart-container/>
    <switcher v-on:theme-value='changeTheme'/>
    <sign/>
  </div>
</template>

<script>
import Card from './components/Card'
import ChartContainer from './components/ChartContainer'
import Sign from './components/Sign'
import Switcher from './components/Switcher'

export default {
  name: 'App',
  components: {
    Card,
    ChartContainer,
    Sign,
    Switcher,
  },
  data() {
    return {
        apiData: null,
        theme: Boolean
    }
  },
  created() {
    this.theme = true;
    fetch(
      'https://onemocneni-aktualne.mzcr.cz/api/v2/covid-19/zakladni-prehled.json')
      .then((response) => response.json())
      .then((data) => this.apiData = data.data[0]); 
  },
  methods: {
    changeTheme() {
      if (this.theme === false){
        this.theme = true;
      }
      else{
        this.theme = false;
      }
    }
  }
};
</script>

<style>
html, 
body {
    height: 100%;
}

#app {
  font-family: 'Courier New', Courier, monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  padding-top: 25px;
  height: 100%;
}

* {
  margin: 0 auto;
}

h2 {
  margin-top: 10px;
}

h1 {
  font-family: 'Courier New', Courier, monospace;
}

.dark {
    color: rgb(173, 173, 173);
}
.dark,body{
  background-color: #1a1919;
  overflow: hidden;
}

.dark > .container > .card {
  background-color: #333538;
}

.bright {
  color: #454442;
}

.bright,body {
  background-color: white;
  overflow: hidden;
}

.bright > .container > .card {
  background-color: rgba(115, 121, 121, 0.333);
}

</style>
