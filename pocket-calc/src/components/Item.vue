<template>
  <div id="allTheFish">
    <h1>{{title}}</h1>
      <!-- <div class="aItem" v-for='item in filteredData' :key='item.id'>

        <img v-if='title.includes("Bugs") || title.includes("Fish")' :src='require("@/assets/"+image+"/NH-Icon-"+item.name.toLowerCase().split(" ").join("").replace("-","")+".png")' 
              alt="" class='photo'>
        <h1>{{item.name}}</h1>

        <h2 v-if='title.includes("Fish")' class='shadow'>Shadow Size: {{item.shadowSize}}</h2>
        <h2>Loction: {{item.loction}} | TOD: {{item.time}}</h2>
        <h3>{{item.value}} Bells</h3>
        <button class='button' @click=spreadFish(item) >+</button>

      </div> -->

  <sui-list divided relaxed>
    <sui-list-item class="aItem" v-for='item in filteredData' :key='item.id'>
      <!-- <sui-list-icon name="github" size="large" vertical-align="middle" /> -->
      <sui-image v-if='image.includes("img")' :src='require("@/assets/img/NH-Icon-"+item.name.toLowerCase().split(" ").join("").replace("-","")+".png")' 
      fluid />
      <sui-list-content>
        <a is="sui-list-header">{{item.name}}</a>
        <a is="sui-list-description">{{item.value}} Bells</a>
        <a is="sui-list-description"
           v-if='title.includes("Fish")' class='shadow'
        >Shadow Size: {{item.shadowSize}}</a>
        <a v-if='title.includes("Bugs") || title.includes("Fish")'
         is="sui-list-description">Loction: {{item.loction}} | TOD: {{item.time}}</a>
          <sui-button color="green" content="Add to Pocket" @click=spreadFish(item) />
         <!-- <a class='button' @click=spreadFish(item) ></button> -->
      </sui-list-content>
    </sui-list-item>
  </sui-list>





  </div>
</template>

<script>

export default {
    name:'Item',
    props:{
      title:String,
      image:String,
      search:String,
      data: Array
    },
    data(){
        return{
        photoLocation: '@/assets/fishPics/NH-Icon-',
        photoEnd: '.png',
        pocketFish:[],
        imgRef:''
        }
    },
    methods:{
      spreadFish(item){
        this.$emit('clickedItem', item)
      },

      addFish(item){
        this.pocketFish.push(item)
        console.log(this.pocketFish)
      },
    },
    computed:{
      filteredData(){
        const filter = new RegExp(this.search, 'i')
        return this.data.filter(data =>data.name.match(filter))
      }, 
    }

}

</script>

<style scoped>
#allTheFish{
  width: 275px;
  padding: 0;
  margin: 0 auto;
  background-color: var(--black-bg);
}
.aItem{
  padding: 5px;
  margin: 7.5px 0 15px 0;
  background-color:var(--tan-bg);
  box-shadow: 5px 5px 5px black;
  max-height: 100px;
  height: 100px;

  object-fit: cover;
  align-content: center;
  justify-content: center;

}
h1{
  margin: 5px 10px 0 0 ;
  padding:5px;
  grid-area: name;
  background-color: #b7b398;
  color:  #f5f7ea; 
  border-radius: 15px;
  padding-left: 15px;
  text-align: left;
  text-transform: uppercase;
  font-size: 2vh;
}
.shadow{
  margin: 0 0 0 0;
  padding:0;
  text-align: left;
  grid-area: shadow;
}
h2{
   margin: 0 0 0 15px;
  padding:0;
  font-size: 1vh;
  text-align: left;
  grid-area: info;
}
h3{
  margin: 0 0 0 15px;
  padding:0;
  font-size: 2vh;
  text-align: left;
  grid-area: value;
}
sui-image{
  grid-area: photo;
  top: 0;
  margin: 0;
  padding: 5px 5px;
  width:100%;
  height: 100%;
  object-fit: cover;
  align-content: center;
  justify-content: center;


}

.button{

  height: 20px;
  line-height: 2px;

  
}




</style>