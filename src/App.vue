<template>
  <div id="app">
    
    <h3>Cadastro: </h3>
    <input type="text" placeholder="Nome" v-model="nomeField"> <br>
    <input type="text" placeholder="E-mail" v-model="emailField"> <br>
    <input type="number" placeholder="Idade" v-model="idadeField"> <br>

    <button @click="cadastrarUsuario">Cadastrar</button>

    <hr>

    <div v-for="cliente in clientes" :key="cliente.id">
      <Cliente :cliente="cliente"
             :showAge="false"
             />
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
      nomeField: "",
      emailField: "",
      idadeField: 0,
      clientes: [
      ]
    }
  },
  components: {
    Cliente
    // Produto
  },
  methods: {
    cadastrarUsuario: function() {
      this.clientes.push({
        id: Date.now(),
        nome: this.nomeField,
        email: this.emailField,
        idade: this.idadeField
      });
      this.limparCampos();
    },
    limparCampos: function() {
      this.nomeField = "";
      this.emailField = "";
      this.idadeField = 0;
    }
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
