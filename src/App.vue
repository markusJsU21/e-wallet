<template>
  <div id="app">
    <Home @toggle-view="toggleView" v-if="currentPage === 'Home'" :cards="cards" @storeUserData="storeData"/>
    <AddCard v-else-if="currentPage === 'AddCard'" @store-user-data="storeData" @toggle-view="toggleView" :cards="cards"/>
  </div>
</template>

//Datan tas emot här. Därefter sickas den till Home genom propen cards. *Gå till Home.

<script>
import {Home, AddCard} from '../src/views/index'

export default {
  components: {Home, AddCard},
  data() { return{
    name: "App",
    currentPage: 'Home',
    cards: [],
    
  }
  },
  methods:{
    storeData(formData){
      this.cards.push(formData)
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
