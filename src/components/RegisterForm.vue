<template>
  <main class="register-form">
      <p v-if="errors.length">
            <b>Please correct the following errors:</b> 
            <ul>
                <li :key="error" v-for="error in errors">*{{error}}</li>
            </ul>
     </p>
      <form @submit.prevent="validate();submit()" @input="updateModel">
        <label for="nr">CARD NUMBER</label>
        <input id="nr" type="text" v-model="user.cardNumber" maxlength="16">
        <label for="name">CARDHOLDER NAME</label>
        <input id="name" type="text" v-model="user.cardHolderName">
        <div class="valid-and-ccv">
          <div class="label-and-input-valid">
            <label for="valid">VALID THRU</label>
            <!-- <input type="text" id="valid" v-model="user.validThru" maxlength="4" placeholder="MMYY"> -->
            <div class="year-and-month">
              <select name="month" id="valid" v-model="user.validThru.month">
                <option v-for="month of months" :key="month" :value="month">{{month}}</option>
            </select>
                <p> / </p>
              <select name="year" id="valid" v-model="user.validThru.year">
                <option v-for="year of validYears" :key="year" :value="year">{{year}}</option>
              </select>
              
            </div>
          </div>
          <div class="label-and-input-ccv">
            <label for="ccv">CCV</label>
            <input id="ccv" type="text" v-model="user.ccv" maxlength="3">
          </div>
        </div>
        <label for="vendor">VENDOR</label>
        <select name="vendor" id="vendor" v-model="user.vendor.name">
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
        id: crypto.randomUUID(),
        cardNumber: '',
        cardHolderName: '',
        validThru: {
          year: '',
          month: '',
        },
        ccv: '',
        vendor: {
            name:'model',
            wifi:'',
        }, 
      },
      errors: [],
      date: new Date(),
      months: ['01', '02', '03', '04', '05', '06',
      '07', '08', '09', '10', '11', '12']
    }
  },
  
  computed:{
      thisYear(){ 
        return  this.date.getFullYear();
      },
      yearPlusOne(){
        return  this.date.getFullYear() + 1;
      },
      validYears(){
        return [ (this.date.getFullYear().toString()), 
        (this.date.getFullYear() + 1).toString(),
        (this.date.getFullYear() + 2).toString(),
        (this.date.getFullYear() + 3).toString(),
        (this.date.getFullYear() + 4).toString(),
        ]
      }
  },      
  methods: {
      validate(){
          if(this.user.cardNumber.length != 16){
            this.errors.push('Card number must be 16 digits.')
            }
            if(this.user.cardHolderName.length == 0){
                this.errors.push('Name must have at least one character.')
            }
            if(this.user.ccv.length < 3){
              this.errors.push('CCV must have 3 digits.')
            }
            if(this.user.vendor.name == 'model'){
              this.errors.push('Please select a bank vendor.')
            }
            for(let card of this.cards){
              if(this.user.cardNumber == card.cardNumber){
                this.errors.push('This card number is already in use.')
              }
            }
      },
      submit(){
        
        if(!this.errors.length){
        this.$emit('send', {...this.user})
         this.$emit('toggle-view')
        }       
      },
      updateModel(){
          this.errors = []
          this.$emit('update-model', {...this.user})
      }
  },
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
        justify-content: space-evenly;
    }
    input, select{
        height: 3rem;
        border-radius:5px;
        border: 0.2px solid black;
        
    }
    #submit-container{
        display: flex;
        justify-content: center;
        width:100%;
    }
    #submit{
        width:100%;
    }
    li{
        color:red;
    }
    .valid-and-ccv{
      width: 100%;
      display:flex;
      flex-direction: row;
      justify-content: space-between;
    }
    .label-and-input-valid, .label-and-input-ccv{
      display:flex;
      flex-direction: column;
      width: 45%;
    }
    .year-and-month{
      display:flex;
      flex-direction: row;
      justify-content: space-between;
    }
    .year-and-month select{
      width: 45%;
    }
    .year-and-month p{
      align-self: center;
      color: rgb(153, 153, 153);
    }
</style>



// /(\d{16}|\d{4}[- ]\d{4}[- ]\d{4}[- ]\d{4}")/g
