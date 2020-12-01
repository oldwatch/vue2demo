<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Account/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Account from "./components/account"

export default {
  name: 'App',
  components: {
    Account
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
