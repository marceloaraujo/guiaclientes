<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
        <!-- objeto cliente sendo passado via prop no App.vue -->
        <h4>Nome: {{ cliente.nome }}</h4>
        <hr>
        <p>Email: {{ cliente.email | processarEmail }}</p>
        <p v-if="showAge">Idade: {{ cliente.idade }}</p>
        <p v-else>O usuário escondeu a idade</p>

        <button @click="mudarCor">Mudar cor!</button>
        <button @click="emitirEventoDelete">Deletar</button>

        <h4>ID especial: {{ idEspecial }}</h4>

    </div>
</template>

<script>
export default {

    data() {
        return {
            isPremium: false
        }
    },
    props: {
        cliente: Object,
        showAge: Boolean
    },
    methods: {
        mudarCor: function() {
            this.isPremium = !this.isPremium;
        },
        emitirEventoDelete: function() {
            console.log('EMITINDO EVENTO...');
            this.$emit('meDelete', {cliente_id: this.cliente.id, component: this});
        }
    },
    filters: {
        processarEmail: function(value) {
            return value.toUpperCase();
        }
    },
    computed: {
        idEspecial: function() {
            return (this.cliente.email + this.cliente.nome + this.cliente.id).toUpperCase();
        }
    }

}
</script>

<style scoped>
    .cliente {
        background-color: #ece5e3;
        max-width: 600px;
        height: 200px;
        padding: 1%;
        margin-top: 5px;
    }

    .cliente-premium {
        background-color: black;
        color: yellow;
        max-width: 600px;
        height: 170px;
        padding: 1%;
        margin-top: 5px;
    }
</style>