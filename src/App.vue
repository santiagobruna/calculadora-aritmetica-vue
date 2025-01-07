<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue'
  import Formulario from './components/Formulario.vue'

  const estado = reactive({
    primeiroNumero: '',
    segundoNumero: '',
    filtro: 'soma', // operação padrão
  })
  function getSoma() {
    return Number(estado.primeiroNumero) + Number(estado.segundoNumero);
  }

  function getSubtracao() {
    return Number(estado.primeiroNumero) - Number(estado.segundoNumero);
  }

  function getDivisao() {
    return Number(estado.primeiroNumero) / Number(estado.segundoNumero);
  }

  function getMultiplicacao() {
    return Number(estado.primeiroNumero) * Number(estado.segundoNumero);
  }
  const filtroDeOperacoes = () => {
    const { filtro } = estado;
    switch(filtro) {
      case 'subtracao':
        return getSubtracao();
      case 'divisao':
        return  getDivisao();
      case 'multiplicacao':
        return  getMultiplicacao();
      default:
        return getSoma();  
    }
  }
  // Funçao para limpar os inputs após a operação
  const limparInputs = () => {
    estado.primeiroNumero = '';
    estado.segundoNumero = '';
  };
</script>

<template>
  <div class="container">
    <Cabecalho/>
    <Formulario 
      :trocar-filtro="evento => (estado.filtro = evento.target.value)"
      :primeiro-numero="evento => (estado.primeiroNumero = evento.target.value)"
      :segundo-numero="evento => (estado.segundoNumero = evento.target.value)"
      :resultado="filtroDeOperacoes()"
      />
  </div>
</template>

<style scoped>

</style>
