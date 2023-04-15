<template>
    <div class="teclado">

        <button class="teclado-botao" 
            v-for="(letra, key) in 'qwertyuiopasdfghjklçzxcvbnm-'" 
            :key="key" 
            :disabled="verificaLetra(letra)"
            v-on:click="jogar(letra)">
            {{ letra }}
        </button>

    </div>
</template>

<script>

export default {
    name: 'Teclado',

    props: {
        letras: Array,
        verificaLetra: Function,
        jogar: Function,

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
.teclado{
    width: 850px;
    margin: 2em 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    text-align: center;
}

.teclado button{
    width: 60px;
    height: 50px;
    margin: .5em;
    font-size: 1.1em;
    font-weight: 500;
    text-transform: uppercase;
    border: solid 1px transparent;
    box-shadow: 0 0 10px 1px rgba(0, 0, 0, .6);
}

.teclado button:focus{
    box-shadow: none;
    border: solid 1px rgba(255, 255, 255, .2);
}

</style>