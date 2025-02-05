<script setup>

  import { reactive } from 'vue';

  const calculo = reactive ({

    numeroUm: 0,
    numeroDois: 0,
    conta: 'somar',
    resultado: 0,

  })

  function addNumero1 (number) {
    calculo.numeroUm = number.target.value;
  }

  function addNumero2 (number) {
    calculo.numeroDois = number.target.value;
  }

  function trocaCauculo(evento) {
    calculo.conta = evento.target.value;

  }

  function calculoReactive () {

    const {numeroUm, conta, numeroDois} = calculo;

    const num1 = Number(numeroUm);
    const num2 = Number(numeroDois);

    switch (conta) {
      case 'somar': return num1 + num2;

      case 'subtrair': return num1 - num2;

      case 'dividir': return num1 / num2;

      case 'multiplicar': return num1 * num2;

    }

  }


</script>

<template>

  <header class="pt-2 pb-2 mb-5 cabecalho">
    <div class="container d-flex justify-content-center">

      <h1>Calculadora Reactive</h1>
      
      <i class="bi bi-calculator-fill fs-2 ms-3"></i>

    </div>
  </header>

  <body>
    
    <form class="container form calculadora">

      <div class="container resultado">

        <p class="campo-de-resultados"><span id="resultado">{{ calculoReactive () }}</span></p>

      </div>

      <div class="container d-flex inputs">

        <input @keyup="addNumero1" class="campo-para-numero" type="number">

        <select @change="trocaCauculo" class="form-control selecoes">
                <option value="somar">+</option>
                <option value="subtrair">-</option>
                <option value="dividir">/</option>
                <option value="multiplicar">x</option>
            </select>

        <input @keyup="addNumero2" class="campo-para-numero" type="number">

      </div>


    </form>

  </body>

</template>

<style scoped>

  .cabecalho {
    background-color: #a5b9dc;
    max-width: 100%;
    align-items: center;
  }

  .calculadora {
    max-width: 300px;
    padding: 22px;
    border-radius: 8px;
    background-color: #747dab;
  }

  .resultado {
    display: flex;
    max-width: 360px;
    height: 48px;
    max-height: 100%;
    border: solid 2px #a5b9dc;
    border-radius: 8px;
    color: #fff;
  }

  .campo-de-resultados {
    width: 100%;
    text-align: center;
    margin: auto 0;
  }

  .inputs {
    width: 280px;
    max-width: 100%;
    justify-content: center;
    margin-top: 6px;
  }

  .campo-para-numero {
    background-color: #747dab;
    border: solid 2px #a5b9dc;
    border-radius: 8px;
    max-width: 40%;
    color: #fff;
  }

  .campo-para-numero::-webkit-inner-spin-button,
  .campo-para-numero::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
}

  .selecoes {
    width: 150px;
    margin-left: 8px;
    margin-right: 8px;
    background-color: #747dab;
    border: solid 2px #a5b9dc;
    color: #fff;
  }

  .selecoes:focus {
    align-items: center;
    background-color: #747dab;
    color: #fff;
  }
  
</style>