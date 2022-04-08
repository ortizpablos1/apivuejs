<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />

    <h1>Bienvenido a la API de Estudiantes</h1>
    <p>Has la practica de consumo con esta API</p>
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
};
</script>
