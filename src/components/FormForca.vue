<template>
    <div class="form">
        <form >
            <div class="form-title">{{ title }}</div>

            <input type="text" class="form-input" placeholder="Escreva..." v-model="inputValue" autofocus/>

            <button :disabled="inputValue.length === 0" v-on:click ="onSubmit">{{ button }}</button>

        </form>
    </div>
</template>

<script>
export default {
    name: 'FormForca',

    props: {
        title: String,
        button: String,
        action: Function,

    },

    data() {
        return {
            inputValue: '',
        }
    },

    methods: {
        onSubmit: function(){
            this.action(this.inputValue);
            this.inputValue = '';
        }
    }
}
</script>

<style scoped>
.form form{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.form-title{
    font-size: 1.1em;
    margin: 1.5em 0 .5em 0;
}

.form-input{
    width: 100%;
    padding: .3em .1em;
    font-size: 1em;
    text-align: center;
    border: solid 2px #000;
    border-radius: 5px;
    color: var(--color-text-dark); 
}

.form-input:focus{
    border-color: var(--color-focus);
}

/* CSS Button esta na ./assets/global.css */
</style>