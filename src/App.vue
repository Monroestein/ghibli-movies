<template>
  <div id="app">
    <Welcoming></Welcoming>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Welcoming from './components/Welcoming.vue'

export default {
  name: 'App',
  components: {
    Welcoming
  }
}
</script>

<style>
#app {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #383335;
  margin-top: 60px;
}
</style>
