<template>
  <div id="app">
    <Welcoming @saveUser="getUser"></Welcoming>
    <Body :user="user"></Body>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Welcoming from './components/Welcoming.vue'
import Body from './components/Body.vue'

export default {
  name: 'App',
  data: function(){
    return {
      user: ""
    }
  },
  components: {
    Welcoming,
    Body
  },
  methods:{
    getUser(user){
        // alert(user)
        this.user = user
    }
  }
}
</script>

<style>

body{
  background: #fffbf4;
}

#app {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c281e;
  margin-top: 60px;
  margin-bottom: 60px;
  box-sizing: content-box;
}
</style>
