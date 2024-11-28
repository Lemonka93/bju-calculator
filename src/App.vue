<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <div id="app">
    <h1>Калькулятор БЖУ и калорий</h1>
    <InputForm />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import InputForm from "./components/InputForm.vue";

export default {
  name: "App",
  components: {
    InputForm,
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
