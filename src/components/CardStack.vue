<template>
  <main class="card-stack">
    <ul>
    <li><ActiveCard :key="bankcard" v-for="bankcard of cards" :card="card" @click="$emit('carddata', bankcard)"/></li>
    </ul>
    <p>testfrånCardstack</p>
  </main>
</template>

<script>
import ActiveCard from './ModelCard.vue'
export default {
    components: {ActiveCard},
    props: ['cards'],

}
</script>

<style>

</style>