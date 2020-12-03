<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <button @click="apiCall">실행</button>
  <HelloWorld msg="미세먼지"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    async apiCall() {
      console.log(process.env.VUE_APP_DUST_API_KEY);
      const res = await axios.get(`http://openapi.airkorea.or.kr
      /openapi/services/rest/MsrstnInfoInqireSvc/getNearbyMsrstnList?
      tmX=244148.546388&tmY=412423.75772&ServiceKey=${process.env.VUE_APP_DUST_API_KEY}&autoload=false`)
      console.log(res);
    }
  },
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
