<script setup>
import { reactive } from 'vue';

const estado = reactive({
  tipo: 'adicao',
  primeiroNumero: 0, 
  segundoNumero: 0,
  mensagemDeErro: 'Essa opção não está registrada, por favor, reinicie o site'
})

function checagem()
{
  if(parseInt(estado.primeiroNumero) || parseInt(estado.segundoNumero) === NaN || Infinity)
  {
    return Math.max(estado.primeiroNumero, estado.segundoNumero)
  }
  else
  {
    return 0
  }
}
function fazConta()
{
  switch(estado.tipo)
  {
    case 'adicao':
      return checagem(), parseInt(estado.primeiroNumero) + parseInt(estado.segundoNumero)

    case 'subtracao':
      return checagem(), parseInt(estado.primeiroNumero) - parseInt(estado.segundoNumero)

    case 'multiplicacao':
      return checagem(), parseInt(estado.primeiroNumero) * parseInt(estado.segundoNumero)

    case 'divisao':
      return checagem(), parseInt(estado.primeiroNumero) / parseInt(estado.segundoNumero)

    default:
      return estado.mensagemDeErro
  }
}

</script>

<template>
  <div class="container">
    <header class="p-5 mt-5 mb-5 bg-secondary rounded-5">
      <h1 class="text-center text-light">Calculadora Aritmética</h1>
    </header>
    <form>
      <div class="row">
        <div class="col-md-5 text-center">
          <input @keyup="evento => estado.primeiroNumero = evento.target.value" type="number" placeholder="Digite um número">
        </div>
        <div class="col-md-3">
          <select @change="evento => estado.tipo = evento.target.value" class="text-center p-2">
            <option value="adicao">+ Adição +</option>
            <option value="subtracao">- Subtração -</option>
            <option value="multiplicacao">x Multiplicação x</option>
            <option value="divisao">/ Divisão /</option>
          </select>
        </div>
        <div class="col-md-4 text-center">
          <input @keyup="evento => estado.segundoNumero = evento.target.value" type="number" placeholder="Digite um número">
        </div>
      </div>
    </form>
    <div class="row">
      <div class="col text-center pt-5">
        <h1>
          {{ fazConta() }}
        </h1>
      </div>
    </div>
  </div>
</template>

<style scoped>
  h1
  {
    font-size: 100px;
  }
  input
  {
    border-radius: 10px;
    font-size: 2em;
    border: 5px solid black;
  }
  select
  {
    font-size: 32px;
    border-radius: 10px;
    border: 3px solid black;
  }
</style>
