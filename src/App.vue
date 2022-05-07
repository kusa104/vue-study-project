<template>
  <div id="app">
<<<<<<< Updated upstream
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
=======
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/sync">Sync</router-link> |
      <router-link to="/async">Async</router-link> |
      <router-link to="/promise">Promise</router-link> |
      <router-link to="/async-await">async & await</router-link> |
      <router-link to="/axios">axios</router-link> |
      <router-link to="/sign-up">signUp</router-link> |
      <router-link to="/login">login</router-link> |
      <router-link to="/DelUser">DelUser</router-link> |
    </nav>
    <router-view/>
>>>>>>> Stashed changes
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
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
