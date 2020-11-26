<template>
  <div> 
    <h1>BrewDog Beers</h1>
    <beers-list :beers="beers"></beers-list>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue'
import {eventBus} from './main.js'

export default {
  data(){
    return {
      beers: [],
      favourite: false,
      selectedBeer: null
    }
  },
  components: {
      "beers-list": BeersList
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then( res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })

    }
  }

</script>


<style scoped>

</style>