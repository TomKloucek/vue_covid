<template>
  <footer>
    <h5 class="podpis">Tomáš Klouček; 2021; made with Vue.js</h5>
  </footer>
</template>

<script>
export default {
  name: 'Sign',
  props: {
    msg: String
  }
}
</script>

<style>
.podpis {
  position: absolute;
  bottom: 10px;
  text-align: center;
  right: 15px;
}
</style>

