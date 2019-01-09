<template>
  <div id="app">
    <h1 class="title">{{ planet.title }}</h1>
    <img class="image" :src="planet.hdurl" />
    <p>{{ planet.description }}</p>
    <div>
      <button class="planet-btn" v-on:click="getMocks">View Today</button>
      <button class="next-btn" v-on:click="Next">View Next</button>
    </div>
  </div>
</template>

<script>
  let counter = 0
  import axios from "axios";

  export default {
    name: "App",
    components: {},
    data() {
      return {
        planet: {},
        planets: [
          { 
            title: 'Pluto',
            description: 'this is the coolest of all planets',
            hdurl: "https://photos1.blogger.com/blogger/1472/901/1600/planet%20step%204.0.jpg"
          },
          {
            title: "earth",
            description: 'The sun peaking behind the Earth',
            hdurl: "http://www.planetsun.org/wp-content/uploads/2011/05/planet-erde.jpg"
          },
          {
            title: "Bowl Earth",
            description: "I'm not sure about this one, but I'm sure someone believes it",
            hdurl: "https://joy2theworld2012.files.wordpress.com/2014/12/flat-earth.jpg"
          },
          {
            title: "SnowGlobe Flat Earth",
            description: 'Flath Earth snowGlobe, These people are smart',
            hdurl: "https://img00.deviantart.net/33ae/i/2018/017/8/4/flat_earth_by_kevron2001-dc0amb0.jpg"
          }
        ]
      };
    },
    created: function() {
      // this.getPlanet()
      this.getMocks();
    },
    methods: {
      // getPlanet() {
      //   axios.get('https://api.nasa.gov/planetary/apod?api_key=H0PSZTXODnpFgc2VU5Xxsh06bGam11sQsPSzpWh0').then( response => {
      //     this.planet = response.data
      //   })
      // }
      getMocks() {
        this.planet = {
          title: "Fire Ball",
          hdurl: "https://news.nationalgeographic.com/content/dam/news/photos/000/126/12683.jpg",
          description: "A random photo of a planet from the internet"
        };
      },
      // generateTimeStamp() {
      //   const currentdate = new Date();
      //   const timeStamp =
      //     currentdate.getFullYear() +
      //     "-" +
      //     currentdate.getMonth() +
      //     1 +
      //     "-" + '0' +
      //     (currentdate.getDate() + counter++)
      //   return timeStamp;
      // },
      Next() {
        // axios
        //   .get(
        //     `https://api.nasa.gov/planetary/apod?date=${this.generateTimeStamp()}&api_key=H0PSZTXODnpFgc2VU5Xxsh06bGam11sQsPSzpWh0`
        //   )
        //   .then(response => {
        //     this.planet = response.data;
        //   });
        if (counter > 3) {
          counter = 0
        }
        this.planet = this.planets[counter++]


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
  .image {
    height: 300px;
    width: 300px;
  }
</style>


