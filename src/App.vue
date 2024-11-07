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

function getNumber1(evento) {
  estado.numero1 = evento.target.value;
  if (estado.numero1 == '')  {
    estado.numero1 = 0;
  }
  estado.numero1 = parseFloat(estado.numero1)
  getOperacao();
}

function getNumber2(evento) {
  estado.numero2 = evento.target.value;
  if (estado.numero2 == '')  {
    estado.numero2 = 0;
  }
  estado.numero2 = parseFloat(estado.numero2)
  getOperacao();
}

function getOperador(evento) {
  estado.operador = evento.target.value;
  getOperacao();
}

const getOperacao = () => {
  switch(estado.operador) {
    case 'subtrair':
      return estado.resultado = (estado.numero1 - estado.numero2);
    case 'somar':
      return estado.resultado = (estado.numero1 + estado.numero2);
    case 'dividir':
      if (estado.numero2 == 0) {
        return estado.resultado = "Undefined";
      }
      return estado.resultado = (estado.numero1 / estado.numero2);
    case 'multiplicar':
      return estado.resultado = (estado.numero1 * estado.numero2);
  }
}
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
  color: #b8b8b8;
}
</style>
