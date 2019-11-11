<template>
  <div class="hello">
      <h2>Find Weather</h2>
    <form v-on:submit.prevent="getResult(query)">
    <input type= "text" placeholder="Enter cityname" v-model="query"/>
    </form>
  </div>
</template>

<script>
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
          alert(query);
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
