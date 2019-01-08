<template>
  <div id="app">
    <h1>{{ planets.title }}</h1>
    <img :src="planets.hdurl" />
    <button v-on:click="Next">View Next</button>
    <button v-on:click="getPlanet">View Today</button>
  </div>
</template>

<script>
  let counter = 1
  import axios from "axios";
  
  export default {
    name: "App",
    components: {},
    data() {
      return {
        planets: {},
      };
    },
    created: function() {
      // this.getPlanet()
      this.getMocks();
    },
    methods: {
      // getPlanet() {
      //   axios.get('https://api.nasa.gov/planetary/apod?api_key=H0PSZTXODnpFgc2VU5Xxsh06bGam11sQsPSzpWh0').then( response => {
      //     this.planets = response.data
      //   })
      // }
      getMocks() {
        this.planets = {
          title: "sometitle",
          hdurl: "image",
          description: "lorem ipsum"
        };
      },
      generateTimeStamp() {
        const currentdate = new Date();
        const timeStamp =
          currentdate.getFullYear() +
          "-" +
          currentdate.getMonth() +
          1 +
          "-" + '0' +
          (currentdate.getDate() + counter++)
        return timeStamp;
      },
      Next() {
        axios
          .get(
            `https://api.nasa.gov/planetary/apod?date=${this.generateTimeStamp()}&api_key=H0PSZTXODnpFgc2VU5Xxsh06bGam11sQsPSzpWh0`
          )
          .then(response => {
            this.planets = response.data;
          });
      }
    }
  };
</script>

<style>
  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>

<!-- nasa api key H0PSZTXODnpFgc2VU5Xxsh06bGam11sQsPSzpWh0 -->
