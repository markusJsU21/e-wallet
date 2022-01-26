<template>
  <main class="card-stack">
    
    <ul>
      <div class="grid-container">
    <li :key="user.id" v-for="user of cards"><ModelCard :user="user" @active-card="activeCard"/></li>
     </div>
    </ul>
   
  </main>
</template>

<script>
import ModelCard from './ModelCard.vue'
export default {
    data(){return{
      activeCardData: {}
    }},
    components: {ModelCard},
    props: ['cards'],
    methods: {
        activeCard(user){
          this.activeCardData = user
          this.$emit('active-card', this.activeCardData)
        }
            
      }
    }


</script>

<style>
  
.grid-container{
  display:grid;
  grid-auto-rows: 2rem;
  height: 400px;
  
}
  
</style>