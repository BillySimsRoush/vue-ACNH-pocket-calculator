<template>
  <div class="container">
    
    <!--<h1 v-for="item in myPocket" :key="item.id" v-bind="myPocket">
          {{item.Fish}} | {{item.Value}} |{{item.quantity}} 
        <sui-button circular icon="chevron circle right" @click="addOne(item.Fish)"/>
    </h1>-->
    <h1>{{pocketTotal}} Bells</h1>
    <sui-card-group :items-per-row="6" id="theItems">
      <sui-card v-for="item in myPocket" :key="item.id">
        <sui-card-content>
          <sui-image src="@/assets/fishPics/NH-Icon-tuna.png" class="right floated" />
          <sui-card-header>{{item.Fish}}</sui-card-header>
          <sui-card-meta>{{item.Value}} Bells </sui-card-meta>
          <!-- <sui-card-description>Elliot requested permission to view your contact details</sui-card-description> -->
        </sui-card-content>
        <sui-card-content extra>
          <sui-container text-align="center">
            <sui-button-group>
              <sui-button basic negative
                 icon="trash alternate outline"
                @click="deleteItem(item.Fish)"
              ></sui-button>
 
            </sui-button-group>
          </sui-container>
        </sui-card-content>
      </sui-card>
    </sui-card-group>
  </div>
</template>

<script>
//components++++++++++++++++++++++++++++++++++


export default {
  name: "Pocket",
  props:{
    myPocket: Array,
    search: String
  },
  components: {
  },
  data() {
    return {
      pocketValue: 0,
    };
  },  

  methods: {
    addOne(name) {
      const index = this.myPocket.findIndex(item => item.Fish === name);
      this.myPocket[index].quantity += 1;
      
    },
    deleteItem(name) {
      const index = this.myPocket.findIndex(item => item.Fish === name);
      this.myPocket.splice(index, 1);
    },

  },
  computed: {
      pocketTotal: function(){
          let value = 0
          this.myPocket.forEach(item=>{
             let itemTotal = (item.Value.replace(',','')*1)
             value += itemTotal
          })
          return value
      },

      
        filterData(){
            const filter = new RegExp(this.search, 'i')
            return this.data.filter(data =>data.Fish.match(filter))
        }

  
  },

};
</script>

<style scoped>
.container {
  background-color: white;
  width: 1300px;
  margin: 0 auto;
}
#theItems {
  padding: 10px;
}
sui-button-group {
  width: 30%;
}
.item {
  background-color: red;
}
</style>