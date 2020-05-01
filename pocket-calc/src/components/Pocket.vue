<template>
  <div class="container">
    <search v-on:filteredData="handleSearch" />
      <h1 >{{myPocket}}</h1>

      <!-- <h1 v-if="myPocket<1" @clickedFish='getFish($event)'>Your pocket is empty</h1>
      <div v-else>
          <h1>You have $   in your pocket</h1>
          <div class='item' v-for="item in myPocket" :key='item.id' v-on:clickedFish='getFish($event)'> 

              <h1>{{item.name}}</h1>
          </div>
          

      </div> -->
      <item title='Northern Fish'
      v-bind:data='allFishes'
      v-bind:search="search"
      @clickedFish='getFish(fish)'/>
      <item title='Bugs'
      v-bind:data='allBugs'
      v-bind:search="search"/>

  </div>
</template>

<script>
//components++++++++++++++++++++++++++++++++++
import Item from '@/components/Item.vue'
import Search     from '@/components/Search.vue'

// data++++++++++++++++++++++++++++++++++++++++++
import fishes from '../assets/fishPrices.json'

export default {
    name:'Pocket',
    props:{
    
    },
    components:{
        Item,
        Search
    },
    data(){
        return{
            allFishes:fishes,
            allBugs:[],
            myPocket:[],
        
        }
    },
    methods:{
        getFish(fish){
            console.log('youMadeIt')
            this.myPocket.push(fish)
            
        },
        handleSearch(query){
            this.search = query
        }


    },
    computed:{

    }

}
</script>

<style scoped>
.container{
    background-color: white;
}
.item{
    background-color: red;
}

</style>