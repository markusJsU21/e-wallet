<template>
  <div id="app">
    <Home @toggleView="currentPage='About'" v-if="currentPage == 'Home'"/>
    <AddCard v-else-if="currentPage == 'AddCard'"/>
  </div>
</template>

<script>
import {Home, AddCard} from '../src/views/index'

export default {
  components: {Home, AddCard},
  data() { return{
    currentPage: 'Home',
  }
  },
}
</script>
