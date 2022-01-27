<template>
  <main class="card" @click="$emit('active-card', user)">
    
      <div class="cardcontainer" :class="user.vendor.name">
      
        <div class="wifi-and-logo">
          <img id="wifi" src="../assets/wifi_white.svg" alt="wifi">
          <img :src="require(`../assets/${imgPath}`)" alt="logo">
        </div>
        <div class="chip">
          <img src="../assets/chip.svg" alt="chip">
        </div>
        <div class="number-container"> 
          <h2>{{n[0]}}{{n[1]}}{{n[2]}}{{n[3]}}</h2> 
          <h2>{{n[4]}}{{n[5]}}{{n[6]}}{{n[7]}}</h2> 
          <h2>{{n[8]}}{{n[9]}}{{n[10]}}{{n[11]}}</h2> 
          <h2>{{n[12]}}{{n[13]}}{{n[14]}}{{n[15]}}</h2>
        </div>
        <div class="small-text-box">
          <p class="small-text">CARDHOLDER NAME</p>
          <p class="small-text">VALID THRU</p>
        </div>
        <div class="name-and-valid">
          <p>{{this.name}}</p>
          <p>{{v[0]}}{{v[1]}}/{{v[2]}}{{v[3]}}</p>
        </div>      
      </div>
    
  </main>
</template>

<script>
//Vi splittar cardNumber till en array av siffror. Sedan fyller vi våra data punkter med datan. När first4 
//har fått 4 digits ska second4 börja fyllas och så vidare
export default {
  props: ['user'],
  computed: {
    imgPath(){
      return `${this.user.vendor.name}.svg`
    },
    n(){
      return this.user.cardNumber
    },
    v(){
      return this.user.validThru
    },
    name(){
      
      return this.user.cardHolderName.toUpperCase()
    },
    
  
  },
}
</script>

<style>
p{
  text-align: center;
}
h2{
  font-weight: normal;
  letter-spacing: .2rem;
  margin:0;
}

.card{
  border-radius:10px;
  background-color:rgba(128, 128, 128, 0);
}
.cardcontainer{
  margin-bottom: 2rem;
  width:382px;
  height: 241px;
  border-radius:10px;
  box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
-webkit-box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
-moz-box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
 

}
.wifi-and-logo{
  margin: 1rem auto 0 auto;
  
}
.chip{
  margin: 0 auto;
}

.wifi-and-logo, .chip, .number-container, .small-text-box, .name-and-valid{
display:flex;
flex-direction: row;
width: 90%;
justify-content: space-between;
}

.number-container{
  margin: 1rem auto .5rem auto;
}
.small-text-box{
  
  margin: auto;
}
.name-and-valid{ 
  padding:0;
  margin: auto;
}
.bitcoin{

  background: linear-gradient(248.04deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 99.07%), #FFAE34;
  /* background-color: var(--bitcoin); */

}
.ninja{
  background: linear-gradient(248.3deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0) 100%), #222222;
  /* background-color: var(--ninja); */
  color:white;
}
.blockchain{
  background: linear-gradient(248.52deg, rgba(0, 0, 0, 0.15) 1.49%, rgba(0, 0, 0, 0) 100%), #8B58F9;
  /* background-color: var(--blockchain); */
  color:white;

}
.evil{
  background: linear-gradient(248.3deg, rgba(0, 0, 0, 0.16) 0%, rgba(0, 0, 0, 0) 100%), #F33355;
  /* background-color: var(--evil); */
  color:white;
}

.model{
  background-color: var(--model);
}


</style>