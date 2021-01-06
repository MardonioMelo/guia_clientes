<template>
  <div id="app">
    <div class="container">
      <div class="columns">
        <div class="column is-half">
          <hr />
          <h2 class="subtitle">Cadastro</h2>
        </div>
      </div>
      <div class="columns">
        <div class="column is-half">
          <div class="field">
            <label class="label">Nome</label>
            <div class="control">
              <input
                class="input"
                type="text"
                placeholder="Nome"
                v-model="nomeField"
              />
            </div>
            <p class="help" id="nomeErro" v-show="deuErro">
              Para cadastar o usuário preencha todos os campos!!
            </p>
          </div>
          <div class="field">
            <label class="label">Email</label>
            <div class="control">
              <input
                class="input"
                type="email"
                placeholder="Email"
                v-model="emailField"
              />
            </div>
          </div>
          <div class="field">
            <label class="label">Idade</label>
            <div class="control">
              <input
                class="input"
                type="number"
                placeholder="Idade"
                v-model="idadeField"
              />
            </div>
          </div>
          <div class="buttons">
            <button class="button is-primary" @click="createUser">
              Cadastrar
            </button>
          </div>
        </div>
      </div>
    </div>
    <hr />
    <div v-for="(cliente) in orderClientes" :key="cliente.id">
    
      <Cliente :cliente="cliente" @meDelete="deleteUser($event)" />
    </div>
  </div>
</template>

<script>
import _ from "lodash";
import Cliente from "./components/Cliente";
//import Produto from './components/Produto.vue'

export default {
  name: "App",
  data() {
    return {
      deuErro: false,
      nomeField: "",
      emailField: "",
      idadeField: "",
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
      var novoArray = this.clientes.filter((cliente) => cliente.id != id);
      this.clientes = novoArray;
    },
  },
  computed: {
    orderClientes() {
      return _.orderBy(this.clientes, ["nome"], ["asc"]);
    },
  },
};
</script>

<style>
#nomeErro {
  color: red;
}
</style>
