<template>
  <div id="app">
    <Home @toggle-view="toggleView" v-if="currentPage === 'Home'" :cards="cards" @storeUserData="storeData"/>
    <AddCard v-else-if="currentPage === 'AddCard'" @store-user-data="storeData" @toggle-view="toggleView" :cards="cards"/>
  </div>
</template>

<script>
import {Home, AddCard} from '../src/views/index'

export default {
  components: {Home, AddCard},
  data() { return{
    currentPage: 'Home',
    cards: [],
  }
  },
  methods:{
    storeData(formData){
      this.cards.push({...formData})
       console.log(this.cards)
    },
    toggleView(){
      if(this.currentPage === 'Home'){
        this.currentPage = 'AddCard'
      }
      else{
        this.currentPage = 'Home'
      }
    }
  }
}
</script>

<style>
  
</style>
