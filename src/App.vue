<template>
  <Customers></Customers>
</template>

<script>
import Customers from './components/Customers.vue'

export default {
  name: 'App',
  components: {
    Customers
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
