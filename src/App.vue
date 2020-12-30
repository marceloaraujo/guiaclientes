<template>
  <div id="app">
    
    <div class="buttons">
      <button class="button is-primary">Primary</button>
      <button class="button is-link">Link</button>
    </div>

    <h3>Cadastro: </h3>
    <small id="nomeErro" v-show="showError">O nome é inválido. Por favor, tente novamente!</small> <br>
    <input type="text" placeholder="Nome" v-model="nomeField"> <br>
    <input type="text" placeholder="E-mail" v-model="emailField"> <br>
    <input type="number" placeholder="Idade" v-model="idadeField"> <br>

    <button @click="cadastrarUsuario">Cadastrar</button>

    <hr>

    <div v-for="cliente in orderClientes" :key="cliente.id">
      <Cliente :cliente="cliente"
             :showAge="false"
             @meDelete="deletarUsuario($event)"
             />
    </div>

  </div>
</template>

<script>

import _ from 'lodash';
import Cliente from './components/Cliente';
// import Produto from './components/Produto';

export default {
  name: 'App',
  data() {
    return {
      showError: false,
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
      if(this.nomeField == "" || this.nomeField == " " || this.nomeField.length < 3) {
        this.showError = true;
        setTimeout(() => this.showError = false, 3000);
      } else {
        this.clientes.push({
          id: Date.now(),
          nome: this.nomeField,
          email: this.emailField,
          idade: this.idadeField
        });
        this.limparCampos();
        this.showError = false;
      }
    },
    limparCampos: function() {
      this.nomeField = "";
      this.emailField = "";
      this.idadeField = 0;
    },
    deletarUsuario: function($event) {
      console.log('RECEBENDO EVENTO DO FILHO...', $event);
      var clienteId = $event.cliente_id;
      var newArray = this.clientes.filter(cliente => cliente.id != clienteId);
      this.clientes = newArray;
    }
  },
  computed: {
    orderClientes: function() {
      return _.orderBy(this.clientes, ['nome'], ['asc']);
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
  #nomeErro {
    color: red;
  }
</style>
