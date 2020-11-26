<template>
  <div> 
    <h1>BrewDog Beers</h1>
    <beers-list :beers="beers"></beers-list>
    <beer-detail :beer="selectedBeer" :favourites=favourites ></beer-detail>
    <ul>
      <li v-for="(beer, index) in favourites" :key="index">{{beer.name}}</li>
    </ul>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue'
import {eventBus} from './main.js'
import BeerDetail from './components/BeerDetail.vue'

export default {
  data(){
    return {
      beers: [],
      favourites: [],
      selectedBeer: null
    }
  },
  components: {
      "beers-list": BeersList,
      "beer-detail": BeerDetail
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then( res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })
    eventBus.$on('favourite-beer', (beer) => {
      this.favourites.push(beer)
    })
  
    }
  }

</script>


<style scoped>

</style>