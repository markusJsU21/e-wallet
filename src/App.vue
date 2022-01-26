<template>
  <div id="app">
    <button id="toggle-button" @click="toggleView">Toggle view</button>
    <button id="clear-cards" @click="clearCards">Delete all cards</button>
    <Home @toggle-view="toggleView" v-if="currentPage === 'Home'" :cards="cards" @storeUserData="storeData"/>
    <AddCard v-else-if="currentPage === 'AddCard'" @store-user-data="storeData" @toggle-view="toggleView" :cards="cards"/>
  </div>
</template>

//Datan tas emot här. Därefter sickas den till Home genom propen cards. *Gå till Home.

<script>
import {Home, AddCard} from '../src/views/index'

export default {
  components: {Home, AddCard},
  mounted(){
    let savedCards = JSON.parse(localStorage.getItem('cards'))
    if(savedCards){
      this.cards = savedCards
    }
    
    },
  data() { return{
    name: "App",
    currentPage: 'Home',
    cards: [],
    
  }
  },
  methods:{
    storeData(formData){
      this.cards.push(formData)
      localStorage.setItem('cards', JSON.stringify(this.cards) )
    },
    toggleView(){
      if(this.currentPage === 'Home'){
        this.currentPage = 'AddCard'
      }
      else{
        this.currentPage = 'Home'
      }
    },
    clearCards(){
            this.cards = []
            localStorage.clear();
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

  body{
    background-color: rgb(50, 45, 78);
  }

  h1{
    font-family: 'Source Sans Pro', sans-serif;
  }
  p, label, button, #submit, h2{
    font-family: 'PT Mono', sans-serif;
    margin: 0;
  }
  .small-text, label{
  font-size: .7rem;
  color:rgb(82, 82, 82);
  margin:1rem 0 .3rem 0;
  }



  button, #submit{
    height: 4rem;
    border: 1px solid black;
    border-radius: 5px;
    font-size: 1.5rem;
    margin: 2rem 0 2rem 0;
    font-weight: bold;
  }
  #submit{
    background-color: black;
    color: white;
  }
  #toggle-button, #clear-cards{
    width: 4rem;
    border:none;
    position:fixed;
    right:85%;
    top:80%;
    margin: 0;
    border-radius: 50%;
    box-shadow: -12px 8px 74px -13px rgba(255, 255, 255, 0.75);
-webkit-box-shadow: -12px 8px 74px -13px rgba(255, 255, 255, 0.75);
-moz-box-shadow: -12px 8px 74px -13px rgba(0, 0, 0, 0.75);
font-size: .8rem;
    transform: rotate(-20deg);
    color: rgb(250, 67, 67);
    background-color:rgb(245, 192, 79);
  }

  #clear-cards{
    right: 15%;
    top: 20%;
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
  border-radius: 10px;
}

</style>
