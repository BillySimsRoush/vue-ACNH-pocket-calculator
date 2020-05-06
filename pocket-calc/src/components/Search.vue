<template>
    <div class="search">
        <input type="text" id="search" name="search" 
        v-on:keyup='filteredData'
        placeholder="Search Items"/>
    </div>
</template>

<script>
export default {
    name:'Search',
    data(){
        return{
            search:''
        }
    },

    methods: {
    filteredData() {
        const query = document.getElementById('search').value;
        this.$emit('filteredData', query);
    }
    }
}
</script>

<style>
#search {
    width:33%;
    font-size:24px;
    font-family: 'Roboto Condensed', sans-serif;
    padding:15px;
    border-radius: 35px;
}
</style>