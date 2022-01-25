<template>
  <main class="register-form">
      
      <form @submit.prevent="submit" @change="updateModel">
<!-- //Testa on key up elller down. -->
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
        <p id="submit-container">
        <input id="submit" type="submit" value="ADD CARD">
        </p>

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
        
      },
      
    }
  },
  methods: {
      submit(){
    
         this.$emit('send', {...this.user})
         this.$emit('toggle-view')
      },
      updateModel(){
          
          this.$emit('update-model', {...this.user})
      }
  }
}
</script>

<style scoped>
    main{
        width: 90%;
    }
    form{
        display:flex;
        flex-direction: column;
        width: 100%;
        
    }
    input, select{
        height: 3rem;
        width: 100%;
        border-radius:5px;
        border-style: none;
    }

    #submit-container{
        display: flex;
        justify-content: center;
        width:100%;
    }

    #submit{
        width:100%;
    }
</style>




