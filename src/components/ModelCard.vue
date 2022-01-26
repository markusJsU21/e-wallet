<template>
  <main class="card" @click="$emit('active-card', user)">
    
      <div class="cardcontainer" :class="user.vendor.name">
      
        <div class="wifi-and-logo">
          <img src="../assets/wifi_white.svg" alt="wifi">
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
          <p>{{user.cardHolderName}}</p>
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
    }

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
.cardcontainer{
  margin-bottom: 2rem;
  padding:0;
  width:382px;
  height: 241px;
  border-radius:10px;
  /* flex-direction: column; */
  box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
-webkit-box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
-moz-box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
overflow:hidden;
}
.wifi-and-logo{
  display:flex;
  flex-direction: row;
  justify-content: space-between;
  width:90%;
  margin: auto;
  
}
.chip{
  display:flex;
  width: 90%;
  margin: .5rem auto;
}

.number-container{
  margin: auto;
  width:90%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.small-text-box{
  display:flex;
  flex-direction: row;
  justify-content: space-between;
  width: 90%;
  margin: auto;
}
.name-and-valid{
  display:flex;
  flex-direction: row;
  justify-content: space-between;
  padding:0;
  width: 90%;
  margin: auto;
}
.bitcoin{
  background-color: var(--bitcoin);
}
.ninja{
  background-color: var(--ninja);
  color:white;
}
.blockchain{
  background-color: var(--blockchain);
  color:white;

}
.evil{
  background-color: var(--evil);
  color:white;
}

.model{
  background-color: var(--model);
}


</style>