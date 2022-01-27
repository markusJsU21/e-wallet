<template>
  <main class="home">
      <h1>E-WALLET</h1>
      
      
        <ModelCard v-if="activecard" :user="activecard"/>
        <p v-if="!cards.length">You haven't added any cards to your wallet yet.</p>

        <div v-if="deleteCard" class="delete-card-box">
            <p>Do you really want to delete this card?</p>
            <button @click="deleteThisCard">Yes</button><button @click="keepCard">No</button>
        </div>
        <button v-if="activecard" @click="deleteCard = !deleteCard">Delete this card</button>
        
        <CardStack @active-card="activateCard" :cards="cards"/>

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
        activecard: this.cards[0],
        deleteCard: false,
    }},
    methods:{
        activateCard(user){
            this.activecard = user
        },
        deleteThisCard(){
            let newCards = []
            if(this.activecard){
                let cardToDelete = this.cards.findIndex(element => element.cardNumber = this.activecard.cardNumber)
                newCards = this.cards.splice(cardToDelete, 1)
            this.cards = newCards
            }
            else if(this.card.length == 1){
                let cardToDelete = this.cards[0]
                newCards = this.cards.splice(cardToDelete, 1)
            this.cards = newCards
            }
            
            this.activecard = null
            this.deleteCard = false
        },
        keepCard(){
            this.deleteCard = false
        }
        
    },


    
    
    
}
</script>

<style scoped>

 button{
    width: 90%;
}
p{
    width: 70%;
    text-align:center;
}
</style>