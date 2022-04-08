<template>
  <div id="app">
    <nav>
      <router-link class="lista" to="/">Inicio</router-link> |
      <router-link class="lista" to="/about">Estudiantes</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 10px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  margin: 0;
}

nav a.router-link-exact-active {
  color: #42b983;
}
.lista {
  text-decoration: none;
  list-style: none;
  font-size: 20px;
}
</style>
