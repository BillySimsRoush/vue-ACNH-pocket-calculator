<template>
  <div id="allTheFish">
      <div class="aFish" v-for='fish in allFishes' :key='fish.id '>
        <div class="photo"></div>
        <h1>{{fish.Fish}}</h1>
        <h2>Shadow Size: {{fish.shadowSize}}</h2>
        <h3>Value: {{fish.Value}}</h3>
      </div>
  </div>
</template>

<script>
import fishes from '../assets/fishPrices.json'
export default {
    name:'Fish',
    data(){
        return{
        allFishes:fishes
        }
    }

}
</script>

<style scoped>
:root{
  --black-bg: #39383d;
  --tan-bg:  #b7b398;
  --white-font: #f5f7ea;
}



#allTheFish{
  width: 500px;
  padding: 0;
  margin: 0 auto;
  background-color: var(--black-bg);
}
.aFish{
  width: 100%;
  padding: 0;
  margin: 7.5px 0;
  background-color:var(--tan-bg);
  display: grid;
  grid-template-columns: 1fr 1fr  1fr;
  grid-template-areas: 
  " photo name name "
  " photo shadow  shadow "
  " photo value value"
  ;
}
h1{
  margin: 10px 10px 0 0 ;
  padding:0;
  grid-area: name;
  background-color: #b7b398;
  color:  #f5f7ea; 
  border-radius: 15px;
  padding-left: 15px;
  text-align: left;
  text-transform: uppercase;
  font-size: 25px;
}
h2{
   margin: 0;
  padding:0;
  font-size: 25px;
  text-align: left;
  grid-area: shadow;
}
h3{
   margin: 0;
  padding:0;
  font-size: 25px;
  text-align: left;
  grid-area: value;
}
.photo{
  grid-area: photo;
  width:200px;
}





</style>