<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import Rodape from './components/Rodape.vue';

const estado = reactive({
  numero1: 0,
  numero2: 0,
  resultado: 0,
  operador: 'somar',
})
</script>

<template>
  <div class="container">
    <Cabecalho />
    <Formulario 
      :getNumero1="numero1"
      :getNumero2="numero2"
      :getResultado="resultado"
      :getOperador="operador"
    />
    <Rodape />  
    
  </div>
  
</template>

<style scoped>
.container {
  max-width: 800px;
  width: 100%;
  color: gray;
}
</style>
