<script setup>
import { reactive } from 'vue';


const states = reactive({
  num1: 0,
  num2: 0,
  operation: 'soma',
})

const sum = () => {
  const { num1, num2 } = states;
  return Number(num1) + Number(num2);
}

const subtract = () => {
  const { num1, num2 } = states;
  return Number(num1) - Number(num2);
}

const multiply = () => {
  const { num1, num2 } = states;
  return Number(num1) * Number(num2);
}

const divide = () => {
  const { num1, num2 } = states;
  return Number(num1) / Number(num2);
}

const getOperation = () => {
  const { operation } = states;

  switch(operation) {
    case 'soma':
      return sum();
    case 'subtração':
      return subtract();
    case 'multiplicação':
      return multiply();
    case 'divisão':
      return divide();
     
  }
}

</script>

<template>
  <div class="container text-center">
    <h1 class="text-center pt-4 pb-4">Calculadora Vue</h1>
    <form class="form">
      <input @keyup="event => states.num1 = event.target.value" class="form-control" type="number" placeholder="Digite o primeiro numero">
        <select class="mt-2 mb-2 form-control" @change="event => states.operation = event.target.value">
          <option value="soma">Somar</option>
          <option value="subtração">Subtrair</option>
          <option value="multiplicação">Multiplicar</option>
          <option value="divisão">Dividir</option>
        </select>
      <input  @keyup="event => states.num2 = event.target.value" class="form-control" type="number" placeholder="Digite o segundo numero">
    </form>
    <div class="result bg-light mt-5 p-3 rounded-2 ">
      <p class="fw-bold">O resultado da {{ states.operation }} dos dois números e igual a:</p>
      <h2 class="fs-1">{{ getOperation() }}</h2>
    </div>
  </div>

</template>

<style scoped>

</style>
