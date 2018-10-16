<template>
  <div id="app">
    <HelloWorld/>
    <!-- <bind/>
    <user/> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Bind from "./components/Bind";
import user from "./components/user"

export default {
  name: 'App',
  components: {
    HelloWorld,
    Bind,
    user
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
