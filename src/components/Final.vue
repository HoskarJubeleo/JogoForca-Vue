<template>
    <div class="final">

        <div :class="`final-texto ${etapa}`">
            {{ texto }}
        </div>
            <button class="final-botao" v-on:click="jogarNovamente">Jogar Novamente</button>

    </div>
</template>

<script>

export default {
    name: 'Final',

    props: {
        etapa: String,
        texto: String,
        jogarNovamente: Function,

    },

    data() {
        return {

        }
    },

    methods: {

    },

    components: {

    }


}
</script>

<style scoped>
    .final-texto{
        margin: 1.5em 0;
        font-size: 1.5em;
        font-weight: bold;
    }

    .final-texto.enforcado{ color: var(--color-text-error); }

    .final-texto.ganhador{ color: var(--color-text-success); }

    .final button{
        font-size: 1.1em;
        font-weight: bold;
        color: var(--color-background);
        background: var(--color-text-success);
    }
</style>