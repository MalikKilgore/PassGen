<template>
  <Password />
</template>

<script>
import Password from "./components/Password.vue";
export default {
  name: "App",
  components: {
    Password
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  widows: 100vw;
  overflow: hidden;
  background-color: #8d8d8d;
}
</style>