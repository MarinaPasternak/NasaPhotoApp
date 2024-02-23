<script setup>
import { ref, onMounted } from 'vue';

import WelcomeScreen from './components/WelcomeScreen.vue';

const isWelcomeScreenShown = ref(true);

onMounted(() => {
  setTimeout(() => {
    isWelcomeScreenShown.value = false
  }, 5000);
});

</script>

<template>
   <transition name="fade">
    <div v-if="isWelcomeScreenShown">
      <WelcomeScreen></WelcomeScreen>
    </div>
  </transition>
</template>

<style>
body {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  background-color: #2c3e50;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 0px;
  padding: 0px;
  overflow: hidden;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
