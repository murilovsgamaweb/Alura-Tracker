<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">
      <Cronometro :tempoEmSegundos="tempoEmSegundos"/>
      <BotoesTemporizador @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
      <BotoesTemporizador @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
    </section>
  </template>

<script lang="ts">
import {defineComponent} from 'vue'
import Cronometro from './CronometroTemporizador.vue';
import BotoesTemporizador from './BotoesTemporizador.vue';

export default defineComponent({
    name:'TemporizadorFormulario',
    emits:['aoTemporizadorFinalizado'],
    components:{
      Cronometro,
      BotoesTemporizador
    },
    data(){
        return{
            tempoEmSegundos:0,
            cronometro : 0,
            cronometroRodando: false
        }
    },

    methods:{
        iniciar(){
            this.cronometroRodando = true
           this.cronometro =  setInterval(()=>{
               this.tempoEmSegundos += 1
            }, 1000)
          
        },
        finalizar(){
            this.cronometroRodando = false
          clearInterval(this.cronometro)
          this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
          this.tempoEmSegundos = 0
        }
    }
})
</script>
