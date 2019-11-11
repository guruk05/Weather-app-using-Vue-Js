<template>
  <div class="hello">
      <h2>Find Weather</h2>
    <form v-on:submit.prevent="getResult(query)">
    <input type= "text" placeholder="Enter cityname" v-model="query"/>
    </form>
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
    query:'guru'
  }
  },
  methods: {
      getResult(query) {
          axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${query}&appid=${key}`)
          .then( response => {
              /* eslint-disable no-console */
console.log(response.data);
// console.log(query);
/* eslint-enable no-console */
              });
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
