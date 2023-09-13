<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue'
  import Formulario from './components/Formulario.vue'
  import Resposta from './components/Resposta.vue'

  const estado = reactive({
    tipo: 'adicao',
    primeiroNumero: 0, 
    segundoNumero: 0,
    mensagemDeErro: 'Essa opção não está registrada, por favor, reinicie o site'
  })

  function checagem()
  {
    if(estado.tipo === 'divisao' && estado.segundoNumero == 0)
    {
      return true
    }
    else if(isNaN(estado.primeiroNumero))
    {
      return true
    }
    else if(isNaN(estado.segundoNumero))
    {
      return true
    }
    else
    {
      return false
    }
  }
  function fazConta()
  {
    switch(estado.tipo)
    {
      case 'adicao':
        if(checagem() == true)
        {
          return 'O(s) campo(s) está(ão) indefinido(s)!'
        }
        else
        {
          return estado.primeiroNumero + estado.segundoNumero
        }

      case 'subtracao':
        if(checagem() == true)
        {
          return 'O(s) campo(s) está(ão) indefinido(s)!'
        }
        else
        {
          return estado.primeiroNumero - estado.segundoNumero
        }

      case 'multiplicacao':
        if(checagem() == true)
        {
          return 'O(s) campo(s) está(ão) indefinido(s)!'
        }
        else
        {
          return estado.primeiroNumero * estado.segundoNumero
        }

      case 'divisao':
        if(checagem() == true)
        {
          return estado.primeiroNumero
        }
        else
        {
          return  estado.primeiroNumero / estado.segundoNumero
        }

      default:
        return estado.mensagemDeErro
    }
  }

</script>

<template>
  <div class="container">
    <Cabecalho />
    <Formulario :getNumber1="evento => estado.primeiroNumero = parseInt(evento.target.value)" :setType="evento => estado.tipo = evento.target.value" :getNumber2="evento => estado.segundoNumero = parseInt(evento.target.value)" />
    <Resposta :fazConta="fazConta()" />
  </div>
</template>

<style scoped>
</style>
