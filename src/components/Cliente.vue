<template>
    <div id="cliente"> 
        <input type="text" :value="nome">
        <hr>
        <input type="text" :value="desc">
        <h2 id="cliente-nome">{{ nome }}</h2>
        <p>Descrição do cliente: {{ desc }}</p>      
    </div>  
</template>

<script>
export default {
    data(){
        return {
            nome: "Mardônio Melo 123 ",
            numero: 0,
            email: "",
            idade: 0,
            desc: "Lorem ipsum 123"
        }
    }
}
</script>

<style scoped>
    #cliente{
     max-width: 600px;
     height: 120px;
    }   
</style>