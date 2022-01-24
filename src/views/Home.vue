<template>
  <main class="home">
      <h1>E-WALLET</h1>
      <p>ACTIVE CARD</p>
      
        <ModelCard v-if="cards.length" :user="activecard"/>
        <p v-else>You haven't added any cards to your wallet yet.</p>
    
        <p>CARDS</p>
        <CardStack @activate-card="activateCard" :cards="cards"/>

        <!-- //varje kort i listan ska få en onclick som först tar bort active classen från alla kort i listan och sedan lägger den på
        //det klickade kortet. Kortets information ska också sparas i en datapunkt som kan heta activecard. Därefter ska ActiveCard anropas med 
        //prop fron activecard. -->

      <button @click="$emit('toggle-view')">ADD A NEW CARD</button>
  </main>
</template>

// I home skall datan tas emot och ett active card skall visas högst upp. Ett kort blir aktivt genom ett klick

<script>
import CardStack from '../components/CardStack.vue'
import ModelCard from '../components/ModelCard.vue'
export default {
    components: {CardStack, ModelCard},
    props: ['cards'],
    created(){
        if(this.cards.length === 1){
                this.cards[0].active = true
                this.activecard = this.cards[0]
            }
        
    },
    data(){return{
        activecard:{},
    }},
    methods: {
        activateCard(){
            
                for(let card of this.cards){
                card.active = false
            }
            this.bankcard.active = true
            this.activecard = this.bankcard
            
            
            
        }
    }
    
}
</script>

<style>

</style>