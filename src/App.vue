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
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro:ital,wght@0,200;0,300;0,400;0,600;0,700;0,900;1,200;1,300;1,400;1,600;1,700;1,900&family=Titillium+Web:wght@200&display=swap');

  :root{
    --evil: #F33355;
    --blockchain: #8B58F9;
    --ninja: #222222;
    --bitcoin: #FFAE34;
    --model: #D7D7D7;
  }

  h1{
    font-family: 'Source Sans Pro', sans-serif;
  }
  p, label, button, #submit{
    font-family: 'PT Mono', sans-serif;
  }
  .small-text, label{
  font-size: .7rem;
  color:rgb(56, 56, 56);
}

  button, #submit{
    height: 3rem;
    border: 1px solid black;
    border-radius: 5px;
    font-size: 1.5rem;
    margin: 2rem 0 2rem 0;
  }
 
  ul{
    list-style: none;
    margin:0;
    padding:0;
  }
  #app{
  display:flex;
  justify-content: center;
  align-content: center;
  margin:0;
  padding:0;
 
}

main{
  width: 414px;
  background-color: rgb(241, 241, 241);
  display:flex;
  flex-direction: column;
  align-items: center;
}

</style>
