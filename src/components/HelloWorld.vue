<template>
  <div class="hello">
    <div v-for="animal in animals" :key="animal.animalName">
      A {{ animal.animalName }} has {{ animal.numberOfLegs }} legs
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data() {
    return {
      url: process.env.VUE_APP_API_URL,
      animals : []
    }
  },
  methods: {
    getAnimals() {
      axios.request({
        method : "GET",
        url : `${this.url}/animals`
      }).then((response)=>{
        this.animals = response.data
      }).catch((error)=>{
        console.log(error);
      })
    }
  },
  mounted () {
    this.getAnimals();
  },
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
