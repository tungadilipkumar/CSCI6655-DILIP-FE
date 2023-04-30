<template>
    <img src="../assets/load.svg" alt="Loading" v-if="btn_disabled"><br>
    <div><p v-if="temperature_data.length"> 

           <span>🌡️ = Temperature in degree F</span>  <span>🇺🇸 = Zip Code - USA</span> <span>🌐 = Latitude & Longitude</span> <span>💧 = Humidity</span> 
           <span>🤖 = Sensor ID</span></p></div>
    <div v-for="data in temperature_data" :key="data['_id']">
        <DataPoint v-bind="data"></DataPoint>
    </div>
    <button @click="publish" :disabled="btn_disabled">{{ btn_text }}</button>
</template>

<style scoped>
span {
  margin: 10px;
  border: 1px solid #8f8f8f;
  border-radius: 4px;
  padding: 5px;
}

div, p {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>

<script>
import DataPoint from './DataPoint.vue';

export default {
  name: 'PublishRandom',
  components: {
    DataPoint,
  }, 
  data () {
    return {
        btn_disabled: false,
        btn_text: "Load data from /api",
        temperature_data: []
    }
  },
  methods: {
    publish() {
        this.btn_disabled = true
        this.btn_text = "loading..."
        this.temperature_data = []
        setTimeout(() => {fetch("http://localhost:3000/api", {
            method: "GET", 
            mode: "cors",
        }).then((response) => {
            this.btn_disabled = false
            this.btn_text = "Load data from /api"
            response.json().then((data) => this.temperature_data = data);
        })}, 900)
    }
  }
}
</script>