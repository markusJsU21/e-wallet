<template>
  <main class="register-form">
      <h1>ADD A NEW BANK CARD</h1>
      <form @submit.prevent="submit" @change="updateModel">

        <label for="nr">CARD NUMBER</label>
        <input id="nr" type="text" v-model="user.cardNumber">
        <label for="name">CARDHOLDER NAME</label>
        <input id="name" type="text" v-model="user.cardHolderName">
        <label for="month">VALID THRU</label>
        <input id="month" type="month" v-model="user.validThru" >
        <label for="ccv">CCV</label>
        <input id="ccv" type="text" v-model="user.ccv">
        <label for="vendor">VENDOR</label>
        <select name="vendor" id="vendor" v-model="user.vendor">
          <option value="bitcoin">BITCOIN INC</option>
          <option value="ninja">NINJA BANK</option>
          <option value="blockchain">BLOCK CHAIN INC</option>
          <option value="evil">EVIL CORP</option>
        </select>
        <button @click="$emit('toggleView')">ADD CARD</button>
      </form>
      
  </main>
</template>

<script>
export default {
    
    props: ['cards'],
    data(){
    return{
      user:{
        id: (this.cards.length),
        cardNumber: '',
        cardHolderName: '',
        validThru: '',
        ccv: '',
        vendor: '',
        img: '',
        active: false, 
      }
    }
  },
  methods: {
      submit(){
          this.$emit('send', {...this.user})
      },
      updateModel(){
          
          this.$emit('updateModel', {...this.user})
      }
  }
}
</script>

<style>

</style>




