<template>
    <button @click="publish" :disabled="btn_disabled">{{ btn_text }}</button>
    <p>{{ response }}</p>
</template>
<style></style>
<script>
export default {
  name: 'PublishRandom',
  data () {
    return {
        btn_disabled: false,
        btn_text: "publish random data",
        response: ""
    }
  },
  methods: {
    publish() {
        this.btn_disabled = true
        this.btn_text = "publishing..."
        this.response = "";
        setTimeout(() => fetch('http://localhost:3000/publish_random', {
            method: "GET", 
            mode: "cors",
        }).then((res) => {
            this.btn_disabled = false
            this.btn_text = "publish random data"
            this.response = "Successfully published data to mqtt broker"
            console.log(res);
        }), 900);
    }
  }
}</script>