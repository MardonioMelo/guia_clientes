<template>
  <div id="app">
    <h3>Cadastro:</h3>
    <small id="nomeErro" v-show="deuErro">
      Para cadastar o usuário preencha todos os campos!!
    </small>
    <br />
    <input type="text" placeholder="nome" v-model="nomeField" /> <br />
    <input type="email" placeholder="email" v-model="emailField" /> <br />
    <input type="number" placeholder="Idade" v-model="idadeField" /> <br />
    <button @click="createUser">Cadastro</button>
    <hr />
    <div v-for="(cliente, index) in orderClientes" :key="cliente.id">
      <h4>Usuário: #{{ index + 1 }}</h4>
      <Cliente :cliente="cliente" @meDelete="deleteUser($event)" />
    </div>
  </div>
</template>

<script>
import _ from 'lodash';
import Cliente from "./components/Cliente.vue";
//import Produto from './components/Produto.vue'

export default {
  name: "App",
  data() {
    return {
      deuErro: false,
      nomeField: "",
      emailField: "",
      idadeField: 0,
      clientes: [
        {
          id: 1,
          nome: "Mardonio1 de melo",
          email: "mardonio1@gmail.com",
          idade: 27,
        },
        {
          id: 2,
          nome: "Andre de melo",
          email: "andre@gmail.com",
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
    cleanForm: function () {
      this.nomeField = "";
      this.emailField = "";
      this.idadeField = "";
    },

    addUser: function () {
      this.clientes.push({
        id: Date.now(),
        nome: this.nomeField,
        email: this.emailField,
        idade: this.idadeField,
      });
    },

    createUser: function () {
      if (
        this.nomeField == "" ||
        this.emailField == "" ||
        this.idadeField == ""
      ) {
        this.deuErro = true;
      } else {
        this.addUser();
        this.cleanForm();
        this.deuErro = false;
      }
    },

    deleteUser: function ($event) {
      console.log("Recebendo evento!");
      var id = $event.idCliente;
      var novoArray = this.clientes.filter(cliente => cliente.id != id)
      this.clientes = novoArray;
    },
  },
  computed: {
    orderClientes(){
      return _.orderBy(this.clientes, ['nome'], ['asc']);
    }
  }
};
</script>

<style>
#nomeErro {
  color: red;
}
</style>
