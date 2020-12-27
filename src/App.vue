<template>
  <div id="app">   
    <input type="text" v-model="clienteMardonio.nome"> 
     <input type="text" v-model="clienteMardonio.idade"> 
    <Cliente :cliente="clienteMardonio" />
   
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
      }
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
