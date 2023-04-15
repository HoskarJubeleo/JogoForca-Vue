<template>
    <div class="palavra">

        <div class="palavra-letras">
            <div :class="`palavra-letra-letra ${etapa}`" v-for="(letra,key) in palavra" :key="key">
                {{ (verificaLetra(letra) || etapa === 'enforcado') ? letra : '' }}
            </div>
        </div>

        <div class="palavra-dica">
            {{dica}}
        </div>

    </div>
</template>

<script>

export default {
    name: 'Palavra',

    props: {
        palavra: String,
        dica: String,
        verificaLetra: Function,
        etapa: String,
        
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
.palavra{
    text-transform: uppercase;
    display: flex;
    flex-direction: column;
    text-align: center;
    align-items: center;
}

.palavra-letras{
    display: flex;

}

.palavra-letra-letra{
    width: 30px;
    height: 30px;
    margin: 0 .5em;
    border-bottom: solid 2px var(--color-text-light);
    display: flex;
    justify-content: center;
    align-items: center;
}

.palavra-letra-letra.enforcado{ color: var(--color-text-error); }
.palavra-letra-letra.ganhador{ color: var(--color-text-success); }

</style>