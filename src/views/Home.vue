<template>
  <main class="home">
      <h1>E-WALLET</h1>
      <p>ACTIVE CARD</p>
      <div class="active-card-container">
          <p>You haven't added any cards to your wallet yet. test2</p>
      </div>
      <CardStack/>

      <button @click="$emit('toggleView')">ADD A NEW CARD</button>
  </main>
</template>

<script>
import CardStack from '../components/CardStack.vue'
export default {
    component: {CardStack}
}
</script>

<style>

</style>