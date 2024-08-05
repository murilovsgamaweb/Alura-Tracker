<template>
<header>
    <h1>
        <img src="../assets/logo.png" alt="">
        
    </h1>
    <button class="button is-large" @click="alterarTema" aria-labelledby="button-label">
     {{textoBotao}}
     <br>
      <span class="icon">
          <i class="fa-regular" :class="iconeBotao"></i>
      </span>
  </button>
</header>
</template>

<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
    name:'BarraLateral',
    emits: ['aoTemaAlterado'],
    data() {
      return {
        modoEscuroAtivo:false
      }
    },

    computed:{
      textoBotao(){
        if(this.modoEscuroAtivo){
          return 'Desativar modo escuro'
        }
        return 'Ativar modo escuro'
      },

      iconeBotao(){
        if(this.modoEscuroAtivo){
          return 'fa-sun'
        }
        return 'fa-moon'
      }
    },
    methods:{
      alterarTema(){
        this.modoEscuroAtivo = !this.modoEscuroAtivo
        this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
      }
    }
})
</script>

<style>
header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
  }

  button i{
    color: #0d3b66;
  }

  img{
    border-radius: 5%;
    border: 3px solid #FFF;
    background: white;
  }
  @media only screen and (max-width: 768px) {
    header {
      padding: 2.5rem;
      height: auto;
    }
  }
</style>
