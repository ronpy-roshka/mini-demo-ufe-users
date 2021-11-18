<template>
  <div id="app">
    <div class="alert alert-success" role="alert">Microfrontend Usuarios</div>

    <Usuarios :user="tarado"/>
  </div>
</template>

<script>
import Usuarios from "./components/Usuarios.vue";

export default {
  name: "App",
  props: {
    tarado: {
      type: String,
      required: false,
    },
  },
  components: {
    Usuarios,
  },
};
</script>

<style lang="scss">
@import "https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
