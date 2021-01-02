<template>
  <div id="app">   
    <input type="text" v-model="clienteMardonio.nome"> 
    <input type="text" v-model="clienteMardonio.idade">     
    <Cliente :cliente="clienteMardonio" :showIdade="true"/>  

    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <h3>Titulo {{index+1}}</h3>    
      <input type="text" v-model="cliente.nome"> 
      <input type="text" v-model="cliente.idade">     
      <Cliente :cliente="cliente" :showIdade="true"/>  
    </div>

  </div>
</template>

<script>
import Cliente from "./components/Cliente.vue";
//import Produto from './components/Produto.vue'

export default {
  name: "App",
  data(){
    return {
      nomeDoMardonio: "Mardonio de M. Filho",
      clienteMardonio: {
        nome: "Mardonio de melo",
        email: "mardonio@gmail.com",
        idade: 31
      },
      clientes: [
        {
          id: 1,
          nome: "Mardonio1 de melo",
          email: "mardonio1@gmail.com",
          idade: 27
        },
        {
          id: 2,
          nome: "Mardonio2 de melo",
          email: "mardonio2@gmail.com",
          idade: 39
        },
        {
          id: 3,
          nome: "Mardonio3 de melo",
          email: "mardonio3@gmail.com",
          idade: 45
        },
        {
          id: 4,
          nome: "Mardonio4 de melo",
          email: "mardonio4@gmail.com",
          idade: 51
        },
      ]
    }
  },
  components: {
    Cliente,
    //   Produto
  },
};
</script>

<style>
</style>
