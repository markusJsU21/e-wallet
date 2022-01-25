<template>
  <main class="card" @click="$emit('active-card', user)">
    
      <div class="cardcontainer" :class="user.vendor.name">
        <div class="wifi-and-logo">
          
          <img src="../assets/wifi_white.svg" alt="wifi">
          <img :src="require(`../assets/${imgPath}`)" alt="logo">
        </div>
        <img src="../assets/chip.svg" alt="chip">
        <p>{{user.cardNumber}}</p>
        <div class="small-text-box">
          <p class="small-text">CARDHOLDER NAME</p>
          <p class="small-text">VALID THRU</p>
        </div>
        <div class="name-and-valid">
          <p>{{user.cardHolderName}}</p>
          <p>{{user.validThru}}</p>
        </div>      
      </div>
    
  </main>
</template>

<script>

export default {
  
  props: ['user'],
  computed: {
    imgPath(){
      return `${this.user.vendor.name}.svg`
    }
  },
  
  
}
</script>

<style>

.cardcontainer{
  padding:.5rem;
  width:382px;
  height: 241px;
  border-radius:10px;
  flex-direction: column;
  box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
-webkit-box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
-moz-box-shadow: -2px 2px 5px -2px rgba(0,0,0,0.75);
}
.wifi-and-logo{
  display:flex;
  flex-direction: row;
  justify-content: space-between;
}
.small-text-box{
  display:flex;
  flex-direction: row;
  justify-content: space-between;
}
.name-and-valid{
  display:flex;
  flex-direction: row;
  justify-content: space-between;
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