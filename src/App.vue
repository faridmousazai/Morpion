<template>
 
  <Morpion msg="Welcome to Noughts and Crosses game"/>
</template>

<script>
import Morpion from './components/Morpion.vue'

export default {
  name: 'App',
  components: {
    Morpion
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
  margin-top: 0px;
}
</style>
