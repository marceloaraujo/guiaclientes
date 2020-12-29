<template>
  <div id="app">
    <Cliente :cliente="cliente"
             :showAge="false"
             />
  </div>
</template>

<script>

import Cliente from './components/Cliente';
// import Produto from './components/Produto';

export default {
  name: 'App',
  data() {
    return {
      cliente: {
        nome: "Marcelo Araujo",
        email: "marcelo.araujo@loupen.com.br",
        idade: 29
      }
    }
  },
  components: {
    Cliente
    // Produto
  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
