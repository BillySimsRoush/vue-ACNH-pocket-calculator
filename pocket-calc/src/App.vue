<template>
  <div id="app">

    <fish/>
  </div>
</template>

<script>

import Fish       from './components/Fish.vue'
export default {
  name: 'App',
  components: {
    Fish
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
