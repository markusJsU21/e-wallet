<template>
  <main class="active-card">
      <div class="cardcontainer">
        <img src="../assets/wifi.svg" alt="wifi">
        <img :src="img" alt="logo">
        <img src="../assets/chip.svg" alt="chip">
        {{activecard.user.cardHolderName}}
        
        <p>testfrånActiveCard</p>
      </div>
  </main>
</template>

<script>

export default {
    props:['activecard'],
    data(){return{
         
    }},
    
   
}
</script>

<style>

</style>