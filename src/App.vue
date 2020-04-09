<template>
  <div>
    <home
      :heroes="heroes"
      :types="types"
      @refetchHeroes="fetchHeroes">
    </home>
  </div>
</template>

<script>
import axios  from 'axios'
import Home from './views/Home'

export default {
  name: "App",
  components: {
    Home
  },
  data () {
    return {
      heroes: [],
      types: []
    }
  },
  methods: {
    fetchHeroes () {
      axios({
        method: "GET",
        url: "http://localhost:3000/heroes"
      })
        .then(({data}) => {
          this.heroes = data
        })
        .catch(err => {
          console.log(err);
        })
    },
    fetchTypes () {
      axios({
        method: "GET",
        url: "http://localhost:3000/types"
      })
        .then(({data}) => {
          this.types = data
        })
        .catch(err => {
          console.log(err);
        })
    }
  },
  created () {
    this.fetchHeroes();
    this.fetchTypes();
  }
}
</script>

<style>
.card {
  border: 0;
  overflow: hidden;
  position: relative;
  box-shadow: 0 0.15rem 1.75rem 0 rgba(30, 40, 50, .15);
}
</style>