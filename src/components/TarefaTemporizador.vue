<template>
  <Box>
    <div class="columns">
      <div class="column is-7">{{ tarefa.descricao }}</div>
      <div class="column">
        <CronometroTemporizador :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
      </div>
    </div>
  </Box>
 
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import CronometroTemporizador from "./CronometroTemporizador.vue";
import ITarefa from "@/interfaces/ITarefa";
import Box from "./Box.vue"


export default defineComponent({
  name: "TarefaTemporizador",
  components: {
    CronometroTemporizador,
    Box
  },
  props:{
    tarefa: {
      type:Object as PropType<ITarefa>,
        required:true
    }
  },
  watch: {
    tarefa(newValue) {
      console.log('Tarefa recebida:', newValue);
    }
  }
});
</script>


