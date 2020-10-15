<template lang='html'>
<div>   
    <ul>
        <list-item v-for="(beer, index) in beers" :beer="beer" :key="index"></list-item>
    </ul>
</div>
</template>

<script>
import BeerItem from './BeerItem';

export default {
    name: 'beer-list',
    props: ['beer'],
    components: {
        'beer-item': BeerItem
    }

}
</script>

<style lang="css" scoped>

</style>