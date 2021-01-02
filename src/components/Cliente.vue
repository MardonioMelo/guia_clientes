<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">        
        <h4>Nome: {{cliente.nome}}</h4> 
        <hr>   
        <p>Email: {{cliente.email}}</p>
        <p v-if="showIdade === true">Idade: {{cliente.idade}}</p>    
        <p v-else>O usuário escondeu a idade!</p>
    </div>  
</template>

<script>
export default {
    data(){
        return {          
            isPremium: false  
        }
    },
    props: {       
        cliente: Object,
        showIdade: Boolean
    }
}
</script>

<style scoped>
    .cliente{
        background-color: bisque;
        max-width: 600px;
        height: 180px;
        padding: 1%;
        font-family: Arial, Helvetica, sans-serif;
        margin-top: 4%;
    }   

    .cliente-premium{
        background-color: black;
        max-width: 600px;
        height: 180px;
        padding: 1%;
        font-family: Arial, Helvetica, sans-serif;
        margin-top: 4%;
        color: aliceblue;
    }   
</style>