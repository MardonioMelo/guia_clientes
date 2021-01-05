<template>
  <div :class="{ cliente: !isPremium, 'cliente-premium': isPremium }">
    <h4>Nome: {{ cliente.nome }}</h4>
    <hr />
    <p>Email: {{ processarEmail }}</p>
    <p v-if="showIdade === true">Idade: {{ cliente.idade }}</p>
    <p v-else>O usuário escondeu a idade!</p>
    <button @click="mudarCor">Mudar cor!</button>
    <button @click="emitirEventoDelete">Deletar</button>
    <h4>Id especial: {{ idEspecial }}</h4>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isPremium: false,
    };
  },
  props: {
    cliente: Object,
    showIdade: Boolean,
  },
  methods: {
    mudarCor: function ($event) {
      console.log($event);
      this.isPremium = !this.isPremium;
    },
    emitirEventoDelete: function () {
      this.$emit("meDelete", {
        idCliente: this.cliente.id,
        curso: "Formação",
        promocao: true,
        component: this,
      });
    },
    testar: function () {
      console.log("testando para valer!");
      alert("ok");
    },
  },
  computed: {
    processarEmail() {
      return "GUIA" + this.cliente.email.toUpperCase();
    },
    idEspecial: function () {
      var str = this.cliente.email + this.cliente.nome + this.cliente.id;
      return str.toUpperCase();
    },
  },
};
</script>

<style scoped>
.cliente {
  background-color: bisque;
  max-width: 600px;
  height: 180px;
  padding: 1%;
  font-family: Arial, Helvetica, sans-serif;
  margin-top: 4%;
}

.cliente-premium {
  background-color: black;
  max-width: 600px;
  height: 180px;
  padding: 1%;
  font-family: Arial, Helvetica, sans-serif;
  margin-top: 4%;
  color: aliceblue;
}
</style>