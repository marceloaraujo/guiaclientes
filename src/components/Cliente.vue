<template>
    <div id="cliente">
        <!-- objeto cliente sendo passado via prop no App.vue -->
        <h4>Nome: {{ cliente.nome }}</h4>
        <hr>
        <p>Email: {{ cliente.email }}</p>
        <p v-if="showAge">Idade: {{ cliente.idade }}</p>
        <p v-else>O usuário escondeu a idade</p>

    </div>
</template>

<script>
export default {

    data() {
        return {
        }
    },
    props: {
        cliente: Object,
        showAge: Boolean
    }

}
</script>

<style scoped>
    #cliente {
        background-color: #ece5e3;
        max-width: 600px;
        height: 150px;
        padding: 1%;
        margin-top: 5px;
    }
</style>