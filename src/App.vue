<template>
  <main id="app">
    <h1>Jogo da Forca</h1>

    <section v-if="tela === 'inicio'" id="inicio">
    
      <FormForca v-if="etapa === 'palavra'" title="Defina a Palavra" button="Próximo" :action="setPalavra"/>
      
      <FormForca v-if="etapa === 'dica'" title="Defina a Dica" button="Iniciar Jogo :)" :action="setDica"/>

    </section>

    <section v-if="tela === 'jogo'" id="jogo">
      <Jogo
            :erros="erros" :palavra="palavra" :dica="dica" 
            :verificaLetra="verificaLetra" :etapa="etapa" 
            :letras="letras" :jogar="jogar" :jogarNovamente="jogarNovamente"
      />
    </section>
  </main>
</template>

<script>

import FormForca from './components/FormForca.vue';
import Jogo from './components/Jogo.vue';

  export default {

    name: 'App',
    data (){
      return {
        tela: 'inicio',
        etapa: 'palavra',
        palavra: '',
        dica: '', 
        erros: 0,
        letras: [],
      }
    },
    components: {
      FormForca,
      Jogo,
      
    },

    methods: {
      setPalavra: function(palavra) {
        this.palavra = palavra;
        this.etapa = 'dica';
      },

      setDica: function(dica) {
        this.dica = dica;
        this.tela = 'jogo';
        this.etapa = 'jogo';
      },

      verificaLetra: function(letra){
        return this.letras.find( item => item.toLowerCase() === letra.toLowerCase());
      },

      jogar: function(letra){
        //ADD letras jogadas
        this.letras.push(letra);

        //VALIDAR erros do jogo
        this.verificarErros(letra);
      },

      verificarErros: function(letra){
        //ACERTO
        if(this.palavra.toLowerCase() .indexOf(letra.toLowerCase()) >= 0){
          return this.vericarAcertos();
        }

        //ERROS placar   
        this.erros++

        //ENFORCADO
        if(this.erros == 6){
          this.etapa = 'enforcado'
        }
      },

      vericarAcertos: function(){
        let letrasUnicas = [...new Set(this.palavra.split(''))]
        if(letrasUnicas.length == (this.letras.length - this.erros)){
          this.etapa = 'ganhador'
        }
      },

      jogarNovamente: function(){
        this.palavra = '';
        this.dica = '';
        this.erros = 0;
        this.letras = [];
        this.tela = 'inicio';
        this.etapa = 'palavra';
      }

    },
  }

  
</script>

<style>
#app{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

</style>
