<template>
  <div id="app">
  <Assignment /> 
          
  </div>
</template>

<script>
import Assignment from './components/Assignment.vue'
export default {
  name: 'app',
  components: {
  Assignment
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
