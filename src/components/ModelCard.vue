<template>
  <main class="card">
      <div class="cardcontainer">
        <img src="../assets/wifi.svg" alt="wifi">
        <img :src= "imgPath" alt="logo">
        <img src="../assets/chip.svg" alt="chip">
        <p>{{user.cardNumber}}</p>
        <p>{{user.cardHolderName}}</p>
        <p>{{user.validThru}}</p>
        <p>{{user.vendor}}</p>
        
        
      </div>
  </main>
</template>

<script>
export default {
  props: ['user'],
  computed: {
    imgPath(){
      return '../assets/' + this.user.vendor + '.svg'
    }
  }
}
</script>

<style>

</style>