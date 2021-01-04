<template>
  <div id="app">
    <h3>Cadastro:</h3>
    <input type="text" placeholder="nome" v-model="nomeField" /> <br />
    <input type="email" placeholder="email" v-model="emailField" /> <br />
    <input type="number" placeholder="Idade" v-model="idadeField" /> <br />
    <button @click="createUser">Cadastro</button>
    <hr />
    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <h3>Usuário: #{{ index + 1 }}</h3>
      <Cliente :cliente="cliente" />
    </div>
  </div>
</template>

<script>
import Cliente from "./components/Cliente.vue";
//import Produto from './components/Produto.vue'

export default {
  name: "App",
  data() {
    return {
      nomeField: "Mardonio de melo",
      emailField: "mardonio@gmail.com",
      idadeField: 31,
      clientes: [
        {
          id: 1,
          nome: "Mardonio1 de melo",
          email: "mardonio1@gmail.com",
          idade: 27,
        },
        {
          id: 2,
          nome: "Mardonio2 de melo",
          email: "mardonio2@gmail.com",
          idade: 50,
        },
      ],
    };
  },
  components: {
    Cliente,
    //   Produto
  },
  methods: {
    createUser: function () {
      this.clientes.push({
        id: Date.now(),
        nome: this.nomeField,
        email: this.emailField,
        idade: this.idadeField,
      });
      this.nomeField = "";
      this.emailField = "";
      this.idadeField = "";
    },
  },
};
</script>

<style>
</style>
