<template>
  <main class="home">
      <h1>E-WALLET</h1>
      <p>ACTIVE CARD</p>
      
        <ActiveCard v-if="cards.length > 0" :activecard="activecard"/>
        <p v-else>You haven't added any cards to your wallet yet.</p>
    

        <CardStack @carddata="cardData"/>

        <!-- //varje kort i listan ska få en onclick som först tar bort active classen från alla kort i listan och sedan lägger den på
        //det klickade kortet. Kortets information ska också sparas i en datapunkt som kan heta activecard. Därefter ska ActiveCard anropas med 
        //prop fron activecard. -->

      <button @click="$emit('toggle-view')">ADD A NEW CARD</button>
  </main>
</template>

<script>
import CardStack from '../components/CardStack.vue'
import ActiveCard from '../components/ActiveCard.vue'
export default {
    components: {CardStack, ActiveCard},
    props: ['cards'],
    data(){return{
        activecard:{},
    }},
    methods: {
        cardData(){
            for(let card of this.cards){
                card.user.active = false
            }
            this.bankcard.active = true
            this.activecard = this.bankcard
            
        }
    }
    
}
</script>

<style>

</style>