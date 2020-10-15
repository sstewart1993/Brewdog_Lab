<template>
  <div id="app">
  </div>
</template>

<script>

import { eventBus } from './main.js';
import beerList from './BeersList';
import beerDetail from './BeerDetail';

export default {
  name: 'App',
  data(){
    return{
      beers: [],
      beerSelected: null
    };
  },

  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) =>{
      this.selectedBeer = beer
    })
  },

  components: {
    'beers-list': BeersList,
    'beer-detail': BeerDetail,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
