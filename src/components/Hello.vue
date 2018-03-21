<template>
  <div class="hello">
    <h2>Doggies from all over the world</h2>
    <ul>
      <li v-for="dogBreed in dogBreeds"> {{ dogBreed }}</li>
    </ul>
  </div>
</template>

<script>
import data from '../data'
export default {
  name: 'hello',
  data () {
    return {
      dogBreeds: []
    }
  },
  created() {
    this.loadDogs()
  },
  methods: {
    loadDogs() {
      this.$http.get('https://dog.ceo/api/breeds/list').then(data=>{
        this.dogBreeds = data.body.message
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0 10px;
}

a {
  color: #35495E;
}
</style>
