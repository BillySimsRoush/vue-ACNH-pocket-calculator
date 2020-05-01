<template>
  <div id="allTheFish">
    <h1>{{title}}</h1>
      <div class="aFish" v-for='fish in data' :key='fish.id '>
        <!-- <img :src="../assets/fishPics/NH-Icon-seabass.png" alt=""> -->
        <!-- <img class='photo' src= require("photoLocation + fish.Fish.toLowerCase() + '.png' ")   /> -->
        <!-- <img :src='photoLocation + fish.Fish.toLowerCase().replace(" ", "") + photoEnd'  class="photo"> -->
        <img :src='require("@/assets/fishPics/NH-Icon-tuna.png")' alt="" class='photo'>
        <h1>{{fish.Fish}}</h1>
        <h2>Shadow Size: {{fish.shadowSize}}</h2>
        <h3>{{fish.Value}} Bells</h3>
        <!-- <button class='button' @click="addFish(fish)" >+</button> -->
        <button class='button' @click=spreadFish(fish) >-</button>
      </div>
  </div>
</template>

<script>

export default {
    name:'Item',
    props:{
      title:String,
      search:String,
      data: Array
    },
    data(){
        return{
        
        photoLocation: '@/assets/fishPics/NH-Icon-',
        photoEnd: '.png',
        pocketFish:[]
        }
    },
    methods:{
      spreadFish(fish){
        this.$emit('clickedFish', fish)
      },

      addFish(fish){
        this.pocketFish.push(fish)
        console.log(this.pocketFish)
      },
    },
    computed:{
      filteredData(){
        const anItem = new RegExp(this.search, 'i')
        return this.data.filter(data =>data.Fish.match(anItem))
 

      }
    }

}

</script>

<style scoped>
#allTheFish{
  width: 300px;
  padding: 0;
  margin: 0 auto;
  background-color: var(--black-bg);
}
.aFish{
  width: 100%;
  height: 75px;
  padding: 0;
  margin: 7.5px 0 0 0;
  background-color:var(--tan-bg);
  box-shadow: 5px 5px 5px black;
  display: grid;
  grid-template-columns: 1fr 1fr  1fr;
  grid-template-areas: 
  " photo name name "
  " photo shadow  shadow "
  " photo value add"
  ;
}
h1{
  margin: 5px 10px 0 0 ;
  padding:0;
  grid-area: name;
  background-color: #b7b398;
  color:  #f5f7ea; 
  border-radius: 15px;
  padding-left: 15px;
  text-align: left;
  text-transform: uppercase;
  font-size: 2vh;
}
h2{
   margin: 0 0 0 15px;
  padding:0;
  font-size: 1vh;
  text-align: left;
  grid-area: shadow;
}
h3{
  margin: 0 0 0 15px;
  padding:0;
  font-size: 2vh;
  text-align: left;
  grid-area: value;
}
.photo{
  grid-area: photo;
  top: 0;
  margin: 0;
  padding: 5px 5px;
  width:75%;
  height: 75%;
  object-fit: cover;
  align-content: center;
  justify-content: center;


}

.button{
  grid-area: add;
  display: flex;
  width: 25px;
  height: 25px;
  border-radius: 50%;
  
}




</style>