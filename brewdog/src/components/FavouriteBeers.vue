<template>
  <div id="favourite-beers">
    <h2>Favourite Beers</h2>
    <ul>
      <li v-for="(beer, index) in favouriteBeers" :key="index">
        {{beer.name}} 
        <!-- <img class="small-beer" :src="beer.image"/> -->
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  name: 'favourite-beers',
  props: ["favouriteBeers"]
}
</script>

<style lang="css" scoped>
</style>
