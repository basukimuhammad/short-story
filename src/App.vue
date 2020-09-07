<template>
  <div id="app">
    <Story msg="CerpenKu 🔥"/>
  </div>
</template>

<script>
import Story from './components/Story.vue'

export default {
  name: 'App',
  components: {
    Story
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
