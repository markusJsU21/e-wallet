<template>
  <main class="add-card">
    <h1>ADD A NEW <br> BANK CARD</h1>
      <ModelCard :user="modelcard"/>
      <RegisterForm @send="register" :cards="cards" @update-model="updateModel" @toggle-view="$emit('toggle-view')"/>
  </main>
</template>

<script>
import RegisterForm from '../components/RegisterForm.vue'
import ModelCard from '../components/ModelCard.vue'
export default {
  data(){return{
    modelcard: {
        cardNumber: '9999999999999999',
        cardHolderName: 'Testperson Persson',
        validThru: {
          year: 'YYYY',
          month: 'MM',
        },
        ccv: '123',
        vendor: {
          name: 'model',
          wifi: '',
        }, 
    }
  }},
  props:['cards'],
  components: {RegisterForm, ModelCard},
  methods: {
    register(formData){
      
      this.$emit('store-user-data', {...formData})
    },
    updateModel(formData){
      this.modelcard = {...formData}
      
    }
    
  }
}
</script>

<style>
  
</style>