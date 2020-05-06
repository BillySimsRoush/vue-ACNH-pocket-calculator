<template>
  <div id="app">
    <search v-on:filteredData="handleSearch" :search='search' class='search'/>

    <pocket v-bind:myPocket='myPocket' class='pocket'/>

    <item title="Fish"
          v-bind:data="allFishes"
          v-bind:search="search"
          @clickedItem="getItem($event)"
          image="img"
          class='fish'
          />
    <item title="Bugs" 
          v-bind:data="allBugs" 
          v-bind:search="search" 
          image="img"
          @clickedItem="getItem($event)"
          class='bug'
          />
    <item title="Shells" 
          v-bind:data="allShells" 
          v-bind:search="search" 
          image="bugPics"
          @clickedItem="getItem($event)"
          class='shell'
          />

          
  </div>
</template>

<script>
import Pocket     from '@/components/Pocket.vue'
import Item       from '@/components/Item.vue'
import Search     from '@/components/Search.vue'
// data++++++++++++++++++++++++++++++++++++++++++
import allFish from "@/assets/allFish.json"
import allBugs from "@/assets/allBugs.json"
import allShells from "@/assets/allShells.json"


export default {
  name: 'App',
  components: {
    Pocket,
    Item,
    Search
  },
  data(){
    return{
      allFishes: allFish,
      allBugs: allBugs,
      allShells:allShells,
      myPocket: [],
      search: ''

    }
  },
  methods:{
      getItem(e) {
        this.myPocket.push(e);
    },
    handleSearch(query) {
      this.search = query;
    }

  }
  
}
</script>

<style >
:root{
  --black-bg: #39383d;
  --tan-bg:  #b7b398;
  --white-font: #f5f7ea;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--black-bg);
  margin-top: 60px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  grid-template-areas: 
  '. search search search .'
  '. pocket pocket pocket .'
  '. fish bug shell.'
  ;
  gap: 10px;
}
body{
  background-color: #39383d;
}
.fish{
  grid-area: fish;
}
.bug{
  grid-area: bug;
}
.shell{
  grid-area: shell;
}
.search{
  grid-area: search;
}
.pocket{
  grid-area: pocket;
}

</style>
