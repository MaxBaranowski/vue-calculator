<template>
  <div id="app">
    <Calculator/>
  </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  name: "app",
  components: {
    Calculator
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  /* background-image: url(/img/triangles-bg.4c69c3c2.png); */
  /* background-size: cover; */
  /* background-repeat: no-repeat; */
  background-color: #fff;
  width: 100vw;
  height: 100vh;
  padding: 0;
  margin: 0;
}
</style>
