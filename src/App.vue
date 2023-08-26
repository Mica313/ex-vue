<script setup>
import { reactive } from 'vue';
const estado = reactive({
  primeiroN:'',
  segundoN:'',
  resultado:'',
  operacao:'adicao'
})
function adicao(){
  return parseInt(estado.primeiroN) + parseInt(estado.segundoN);
}
function subtracao(){
  return parseInt(estado.primeiroN) - parseInt(estado.segundoN)
}
function multiplicacao(){
  return parseInt(estado.primeiroN) * parseInt(estado.segundoN)
}
function divisao(){
  return parseInt(estado.primeiroN) / parseInt(estado.segundoN)
}
function escolheOP(){
  if(estado.operacao == 'adicao'){
    return adicao();
  }else if(estado.operacao == 'subtracao'){
    return subtracao();
  }else if(estado.operacao == 'multi'){
    return multiplicacao();
  }else if(estado.operacao == 'divisao'){
    return divisao();
  }
}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 rounded-3">
      <h1>Calculadora Vue</h1>
    </header>
    <div class="row">
      <div class="body--c col-md-6">
        <input @keyup="evento => estado.primeiroN = evento.target.value" class="form-control m-2 p-1" placeholder="digite o primeiro valor">
        <input @keyup="evento => estado.segundoN = evento.target.value"  class="form-control m-2 p-1" placeholder="digite o segundo valor">
        RESULTADO: {{ escolheOP() }}
      </div>
      <div class="select col-md-2 ms-4">
        <select @change="evento => estado.operacao = evento.target.value" class="form-control">
          <option value="adicao">Adição</option>
          <option value="subtracao">Subtração</option>
          <option value="multi">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .result{
    text-align: center;
    display:flex;
    align-items: center;
    font-family: sans-serif;
    font-size:20px;
  }
  .result span{
    
    border:1px solid black;
    border-radius: 9%;
  }
  .col-md-2{
    padding:0;
  }
  .body--c input{
    max-width: 250px;
  }
  .body--c{
    display: flex;

  }
</style>
