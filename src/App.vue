<template>
  <div id="app">
    
    <div v-for="cliente in clientes" :key="cliente.id">
      <Cliente :cliente="cliente"
             :showAge="false"
             />
      
      <hr>
      <h4>Edição: </h4>
      <input type="text" v-model="cliente.nome">
      <input type="text" v-model="cliente.email">
    </div>

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
      },
      clientes: [
        {
          id: 1,
          nome: "Michael Scott",
          email: "michael@loupen.com.br",
          idade: 23
        },
        {
          id: 2,
          nome: "Marcelo Araujo",
          email: "marcelo.araujo@loupen.com.br",
          idade: 29
        },
        { 
          id: 3,
          nome: "Bruce Wayne",
          email: "bruce@wayneenterprises.com",
          idade: 35
        }
      ]
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
