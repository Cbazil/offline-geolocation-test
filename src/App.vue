<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h2>{{ lat }}</h2>
    <h2>{{ long }}</h2>
    <h2>{{ accu }}</h2>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      lat: 0,
      long: 0,
      accu: 0,
       options: {
        enableHighAccuracy: true,
        timeout: 5000,
        maximumAge: 0
      }
    }
  },
  methods: {
    success (pos) {
      let coords = pos.coords;
      this.lat = coords.latitude;
      this.long = coords.longitude;
      this.accu = coords.accuracy;
    },
    error (err) {
      console.warn(err.message)
    }
  },
  created() {
    navigator.geolocation.getCurrentPosition(this.success,this.error,this.options)
  }
}
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
</style>
