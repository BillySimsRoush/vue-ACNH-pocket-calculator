<template>
  <div id="app">
    <search v-on:filteredData="handleSearch" :search='search'/>

    <pocket v-bind:myPocket='myPocket' />

    <item
      title="Northern Fish"
      v-bind:data="allFishes"
      v-bind:search="search"
      @clickedFish="getFish($event)"
    />
    <item title="Bugs" v-bind:data="allBugs" v-bind:search="search" />
  </div>
</template>

<script>
import Pocket     from '@/components/Pocket.vue'
import Item       from '@/components/Item.vue'
import Search     from '@/components/Search.vue'
// data++++++++++++++++++++++++++++++++++++++++++
import fishes from "@/assets/fishPrices.json"


export default {
  name: 'App',
  components: {
    Pocket,
    Item,
    Search
  },
  data(){
    return{
      allFishes: fishes,
      allBugs: [],
      myPocket: [],
      search: ''

    }
  },
  methods:{
      getFish(e) {
        this.myPocket.push(e);
    },
    handleSearch(query) {
      this.search = query;
    }

  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--black-bg);
  margin-top: 60px;



}
:root{
  --black-bg: #39383d;
  --tan-bg:  #b7b398;
  --white-font: #f5f7ea;
}
body{
  background-color: #39383d;
}

</style>
