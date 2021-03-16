<template>
  <div class="container">
    <div class="card infected">
      <h3>Infected</h3>
      <h4>{{ apiData.aktivni_pripady }}</h4>
      <img src="../icons/mask.svg" alt="Mask">
    </div>
    <div class="card recovered">
      <h3>Recovered</h3>
      <h4>{{ apiData.vyleceni }}</h4>
      <img src="../icons/health.svg" alt="Recovered">
    </div>
    <div class="card death">
      <h3>Death</h3>
      <h4>{{ apiData.umrti }}</h4>
      <img src="../icons/death.svg" alt="Death">
    </div>
    <div class="card vaccinated">
      <h3>Vaccinated</h3>
      <h4>{{ Math.round(apiData.vykazana_ockovani_celkem/2) }}</h4>
      <img src="../icons/vaccine.svg" alt="Vaccine">
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
@media screen and (max-width: 480px) {
.container {
  margin-top: 15px;
  width: 95%;
  display: inline-flex;
  justify-content: space-between;
}


.card {
  padding-top: 10px;
  width: 22%;
  height: 100px;
  border-radius: 3px;
}

img {
  margin-top: 5px;
  height: 40px;
  width: 40px
}

h3 {
  font-size: 12px;
}

h4 {
  font-size: 15px;
}

h1 {
  margin-top: 30px;
}

canvas {
  margin-top: 10px;
}

}

@media screen and (min-width: 481px) {

.container {
  margin-top: 15px;
  width: 60%;
  display: inline-flex;
  justify-content: space-between;
}


.card {
  padding-top: 10px;
  width: 22%;
  height: 175px;
  border-radius: 3px;
}

img {
  margin-top: 10px;
  height: 80px;
  width: 80px
}

}


.card.h3 {
  color: #a19fa1;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
    Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.card.h4 {
   color: #a19fa1;
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
