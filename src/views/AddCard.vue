<template>
  <main class="add-card">
      <ModelCard :user="modelcard"/>
      <RegisterForm @send="register" :cards="cards" @update-model="updateModel" @toggle-view="$emit('toggle-view')"/>
  </main>
</template>

<script>
import RegisterForm from '../components/RegisterForm.vue'
import ModelCard from '../components/ModelCard.vue'
export default {
  data(){return{
    modelcard: {}
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