<template>
  <main class="home">
      <h1>E-WALLET</h1>
      
      
        <ModelCard v-if="activecard" :user="activecard" :cards="cards"/>
        <p v-if="!cards.length">You haven't added any cards to your wallet yet.</p>

        <div v-if="deleteCard" class="delete-card-box">
            <p>Do you really want to delete this card?</p>
            <button @click="deleteThisCard">Yes</button><button @click="keepCard">No</button>
        </div>
        <button v-if="activecard" @click="deleteCard = !deleteCard">Delete this card</button>
        <CardStack v-if="!(cards.length===1)" @active-card="activateCard" :cards="cards"/>

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
    data(){return{
        activecard: this.cards[0],
        deleteCard: false,      
    }},

    // computed:{
    //     activateSingleCard(){
    //        if(this.cards < 2){
    //            return this.activecard = this.cards[0]
    //        } 
    //     }
    // },

    methods:{
        activateCard(user){
            this.activecard = user
        },
        
        keepCard(){
            this.deleteCard = false
        },
        deleteThisCard() {
            const cardToDelete = {...this.activecard}
            this.$emit('deleteThisCard', cardToDelete)
            this.activecard = null
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