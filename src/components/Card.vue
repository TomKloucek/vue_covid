<template>
  <div class="container">
    <div class="card infected">
      <h3>Infected</h3>
      <h4>{{ apiData.aktivni_pripady }}</h4>
    </div>
    <div class="card recovered">
      <h3>Recovered</h3>
      <h4>{{ apiData.vyleceni }}</h4>
    </div>
    <div class="card death">
      <h3>Death</h3>
      <h4>{{ apiData.umrti }}</h4>
    </div>
    <div class="card vaccinated">
      <h3>Vaccinated</h3>
      <h4>{{ apiData.vykazana_ockovani_celkem/2 }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: ['apiData']
};
</script>

<style>
.container {
  margin-top: 5%;
  width: 60%;
  display: inline-flex;
  justify-content: space-between;
}

.card {
  padding-top: 13px;
  width: 22%;
  height: 250px;
  background-color: #e1e3e6;
  border-radius: 3px;
  -webkit-box-shadow: 10px 10px 11px -7px rgba(117, 116, 117, 1);
  -moz-box-shadow: 10px 10px 11px -7px rgba(117, 116, 117, 1);
  box-shadow: 10px 10px 11px -7px rgba(117, 116, 117, 1);
}

.card.h3 {
  color: #4a444d;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
    Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.card.death {
  border-top: 5px solid #c44037;
}

.card.recovered {
  border-top: 5px solid #635bba;
}

.card.infected {
  border-top: 5px solid #53db56;
}

.card.vaccinated {
  border-top: 5px solid #a553cf;
}
</style>
