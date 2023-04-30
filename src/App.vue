<template>
  <h1>Frontend to fetch and see temperature data from Node.js and MongoDB backend</h1>
   <p>As we do not have real sensors, we use the 'publish random data' button to send a request to backend which
    generates random sensor data and publishes using mqttclient
   </p>
  <TemperatureData></TemperatureData>
  <PublishRandom></PublishRandom>
</template>

<script>
import PublishRandom from './components/PublishRandom.vue'
import TemperatureData from './components/TemperatureData.vue'

export default {
  name: 'App',
  components: {
    PublishRandom,
    TemperatureData,
  }
}
</script>

<style>

img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

button {
  margin: 10px;
}
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
