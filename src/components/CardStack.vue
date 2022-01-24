<template>
  <main class="card-stack">
    <ul>
    <li :key="user.id" v-for="user of cards" @click="$emit('activate-card', user)"><ModelCard :user="user"/></li>
    </ul>
  </main>
</template>

<script>
import ModelCard from './ModelCard.vue'
export default {
    components: {ModelCard},
    props: ['cards'],

}
</script>

<style>

</style>