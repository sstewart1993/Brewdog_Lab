<template>
<div v-if="beer">
    <h3>{{ beer.name }}</h3> 
    <p>Percentage: {{ beer.abv }}</p> 
    <p>TagLine: {{ beer.tagline}}</p>
    <img class="small-bottle" :src="beer.image_url">

</div>
  
</template>

<script>
export default {
    name: 'beer-detail',
    props: ['beer']
}
</script>

<style>

</style>