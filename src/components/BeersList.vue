<template>
  <ul>
      <beer-list-item v-for="(beer, id) in beers" :beer="beer" :key="id">{{ beer.name}}</beer-list-item>
  </ul>
</template>

<script>
import BeerListItem from './BeerListItem.vue'
export default {
    name: 'beers-list',
    props: ['beers'],
    components: {
        "beer-list-item": BeerListItem
    }

}
</script>

<style scoped>

</style>