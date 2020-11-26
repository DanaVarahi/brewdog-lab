<template>
  <section v-if="beer">
      <h1>{{ beer.name}}</h1>
      <p>{{beer.abv}}%</p>
      <button  v-on:click="saveFavourite(beer)">Add to Favourites</button>
  </section>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'beer-detail',
    props: ['beer', 'favourites'],
    methods: {
        saveFavourite(){
           eventBus.$emit('favourite-beer', this.beer)
        }
    }    
}
</script>

<style scoped>

</style>