<template>
  <div id="app">
    <h1>BREWDOG BARK!!!!!</h1>
  <div class="main-container"> 
    <beers-list :beers='beers'></beers-list>
    <beer-detail :beer='beerSelected'></beer-detail>

    <favourite-beers :favouriteBeers='favouriteBeers'></favourite-beers>
  
  <button v-on:click="addToFavourites">Add Beer</button>
  
  </div>
  </div>
</template>

<script>

import { eventBus } from './main.js';
import BeersList from './components/BeersList.vue';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeers from './components/FavouriteBeers';

export default {
  name: 'App',
  data(){
    return{
      beers: [],
      beerSelected: null,
      favouriteBeers: []
    };
  },

  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) =>{
      this.beerSelected = beer
    })
  },

  components: {
    'beers-list': BeersList,
    'beer-detail': BeerDetail,
    'favourite-beers': FavouriteBeers,
  },
  methods: {

    addToFavourites: function(){
        this.favouriteBeers.push(this.beerSelected)
      }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
  background-image: url("./components/static/brewdog.jpg");
  font-weight: bold;
}
ul{
  list-style: none;
}
.small-bottle {
  height: 200px
}

</style>
