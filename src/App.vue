<template>
  <div id="app">
    <p class="font-weight-bold" style="font-size: 24pt">Typing Speed Test</p>
    <img src="./assets/logo.png" alt="" />
    <TypingSpeedTest/>
  </div>
</template>

<script>
import TypingSpeedTest from "./components/TypingSpeedTest.vue";

export default {
  name: "App",
  components: {
    TypingSpeedTest,
  },
};
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