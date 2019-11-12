<template>
<div>
      <h2>Find Weather</h2>
    <form v-on:submit.prevent="getResult(query)">
    <input type= "text" placeholder="Enter cityname" v-model="query"/>
     </form>
 
         <h3 class="city" id="showCity" ref="showCity">{{city}}</h3>, <h3 class="state" id='showCountry' ref="showCountry" nbsp>{{country}}
            </h3>
             <!-- <div class="DateTime"> -->
               <!-- <span class="dtDay">Friday</span> -->
                <!-- <span class="dtTime">8:00 am</span> -->
                <!-- </div> -->
                <div class = "icon" > <img id="weatherIcon" v-bind:src="icon" alt="Weather icon"> </div>
                 <div class="weather" id="showDescription" ref="showDescription" >{{climate}}</div>
                <br>
                <div class="degreeSec">
                <div v-on:click="this.showCelsius()" class="dsDegree" id="showDegree" ref="dsDegree">{{celsius}} {{convfahrenheit}}&deg;C </div>
             <div class="Celsius" id="showFahrenheit" ref="showFahrenheit" >{{fahrenheit}}&deg;C </div>
            <!-- <span>|</span> -->
        </div>
  </div>
</template>

<script>
import axios from 'axios';
// let cityName = "chennai";
const key = "2ebbc925a11c3ea05fe72bb48f8ad49d";

export default {
  name: 'HelloWorld',
  data () {
    return {
    msg: 'search',
    query:'',
    city:'',
    country:'',
    celsius: '',
    fahrenheit:'',
    climate:'',
    icon:'',
    convfahrenheit:'',
  }
  },
  methods: {
      getResult(query) {
          axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${query}&appid=${key}`)
          .then( response => {
                /* eslint-disable no-console */
                const data = response.data;
                // this.showCelsius(data);
                let celsius = Math.round(parseFloat(data.main.temp) - 273.15);
                let fahrenheit = Math.round(((parseFloat(data.main.temp) - 273.15) * 1.8) + 32);
                let city = data.name;
                let country = data.sys.country;
                let description = data.weather[0].description;
                let iconcode = data.weather[0].icon;
                let iconurl = "http://openweathermap.org/img/w/" + iconcode + ".png";
                this.celsius = celsius;
               
                // this.results = response 
                // console.log(this.$refs.dsDegree.celsius)
                // console.log(query);
                /* eslint-enable no-console */
              });
              },
               showCelsius(data) {
                 
              }
      }

  }

</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
