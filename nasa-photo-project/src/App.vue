<template>
  <WelcomeScreen></WelcomeScreen>
</template>

<script>
import WelcomeScreen from './components/WelcomeScreen.vue';


export default {
    name: 'App',
    components: { WelcomeScreen }
}
</script>

<style>
body {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
  padding: 0px;
  overflow: hidden;
}
</style>
