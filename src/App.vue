<template>
  <div id="app">
    <BuscarCep />
  </div>
</template>

<script>
import BuscarCep from "./components/BuscarCep.vue";

export default {
  name: "App",
  components: {
    BuscarCep
  }
};
</script>

<style>
body {
  background: #eee;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
