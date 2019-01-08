<template >
  <div v-if='!daily' id="app">
    <Monthly></Monthly>
  </div>
  <div v-else='daily' id="app">
    <h1>{{todaysPlanets.title}}</h1>
    <img :src=todaysPlanets.hdurl />
    <button v-on:click='monthly'>
      View Monthly
    </button>
  </div>
</template>

<script>
import axios from 'axios';
import Monthly from './components/Monthly'

export default {
  name: 'App',
  components: {
    Monthly
  },
  data() {
    return {
      todaysPlanets: {},
      daily: true
    }
  },
  created: function() {
    // this.getPlanet()
    this.getMocks()
  },
  methods: {
    // getPlanet() {
    //   axios.get('https://api.nasa.gov/planetary/apod?api_key=H0PSZTXODnpFgc2VU5Xxsh06bGam11sQsPSzpWh0').then( response => {
    //     this.todaysPlanets = response.data
    //   })
    // }
    getMocks() {
      this.todaysPlanets = {
        title: 'sometitle',
        hdurl: 'image',
        description: 'lorem ipsum'
      }
    },
    monthly() {
      this.daily = false
    }

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<!-- nasa api key H0PSZTXODnpFgc2VU5Xxsh06bGam11sQsPSzpWh0 -->
