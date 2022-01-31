<template>
  <main class="home">
      
      <div v-if="deleteCard" class="fade-layer"></div>
        <h1>E-WALLET</h1>
        
        
            <ModelCard v-if="activecard" :user="activecard" :cards="cards"/>
            <p v-if="!cards.length">You haven't added any cards to your wallet yet.</p>

            <transition name="fade">
            <DeleteCard v-if="activecard" :activecard="activecard" :deletecard="deleteCard" 
            @deleteThisCard="deleteThisCard" @keepCard="keepCard" @remove-box="deleteCard = !deleteCard" />
            </transition>
            <CardStack v-if="cards.length > 1" @active-card="activateCard" :cards="cards"/>

        <button @click="$emit('toggle-view')">ADD A NEW CARD</button>
      
  </main>
</template>

// I home skall datan tas emot och ett active card skall visas högst upp. Ett kort blir aktivt genom ett klick

<script>
import CardStack from '../components/CardStack.vue'
import ModelCard from '../components/ModelCard.vue'
import DeleteCard from '../components/DeleteCardDialog.vue'
export default {
    components: {CardStack, ModelCard, DeleteCard},
    props: ['cards', 'activecard'],
    data(){return{
        deleteCard: false,
        activeCardData: {}      
    }},

    methods:{
        activateCard(user){
            this.activeCardData = user
            this.$emit('activate-card', this.activeCardData)
        },
        
        keepCard(){
            this.deleteCard = false
        },
        deleteThisCard() {
            const cardToDelete = {...this.activecard}
            this.$emit('deleteThisCard', cardToDelete)
            
            this.deleteCard = false
        }
        
    },


    
    
    
}
</script>

<style scoped>
.home{
    position:relative;
}
.fade-layer{
    height:100%;
    width:100%;
    background-color: rgba(0, 0, 0, 0.466);
    position:absolute;
    z-index: 2;
}

.fade-enter-active, .fade-leave-active {
  transition: .2s;
}
.fade-leave-active {
  opacity: 0;
}

 button{
    width: 90%;
}
p{
    width: 70%;
    text-align:center;
}
</style>