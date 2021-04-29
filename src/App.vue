<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Formulari class="col-6 m-auto"></Formulari>
  </div>
</template>

<script>
import Formulari from './components/Formulari.vue'

export default {
  name: 'App',
  components: {
    Formulari
  }
}
</script>
npm cache verify<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
