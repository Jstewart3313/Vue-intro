<template>
  <div id="app">
    <h1>{{todaysPlanets.title}}</h1>
    <img :src=todaysPlanets.hdurl />
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      todaysPlanets: {}
    }
  },
  created: function() {
    this.getPlanet()
  },
  methods: {
    getPlanet() {
      axios.get('https://api.nasa.gov/planetary/apod?api_key=H0PSZTXODnpFgc2VU5Xxsh06bGam11sQsPSzpWh0').then( response => {
        this.todaysPlanets = response.data
      })
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
