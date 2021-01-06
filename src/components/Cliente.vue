<template>
  <div class="container">
    <div class="columns">
      <div class="column is-one-third">
        <div class="card">
          <header class="card-header">
            <p class="card-header-title">{{ cliente.nome }}</p>
            <a href="#" class="card-header-icon" aria-label="more options">
              <span class="icon">
                <i class="fas fa-angle-down" aria-hidden="true"></i>
              </span>
            </a>
          </header>
          <div class="card-content" :class="{ cliente: !isPremium, 'cliente-premium': isPremium }">
            <div class="content">
              <p>
                Email: {{ processarEmail }}<br />
                <span v-if="showIdade === true"
                  >Idade: {{ cliente.idade }}<br
                /></span>
                <span v-else>O usuário escondeu a idade!<br /></span>
                Id especial: {{ idEspecial }}
              </p>             
              <time>{{ dateHora }}</time>
            </div>
          </div>
          <footer class="card-footer">
            <a class="card-footer-item" @click="mudarCor">Mudar cor!</a>
            <a href="#" class="card-footer-item" @click="emitirEventoDelete">Delete</a>
          </footer>
        </div>
      </div>
    </div>
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
    dateHora() {
      // Obtém a data/hora atual
      var data = new Date();

      // Guarda cada pedaço em uma variável
      var dia = data.getDate(); // 1-31
     
      var mes = data.getMonth(); // 0-11 (zero=janeiro)
   
      var ano4 = data.getFullYear(); // 4 dígitos
      var hora = data.getHours(); // 0-23
      var min = data.getMinutes(); // 0-59
      var seg = data.getSeconds(); // 0-59
 

      // Formata a data e a hora (note o mês + 1)
      var str_data = dia + "/" + (mes + 1) + "/" + ano4;
      var str_hora = hora + ":" + min + ":" + seg;

      // Mostra o resultado
      return str_hora + " - " + str_data
    },
  },
};
</script>

<style scoped>
.cliente {
  background-color: rgb(255, 255, 255);
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