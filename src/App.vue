<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Recipe msg="Welcome to Your Vue.js App"/>
</template>

<script>
import Recipe from './components/RecipeComp.vue'

export default {
  name: 'App',
  components: {
    Recipe
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
