<template>
    <div class="box has-text-wight-bold">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name:'BoxTemporizador'
})
</script>

<style scoped>
.box{
  background:#FAF0CA;
}

.column{
  color:#000;
  
}
</style> 