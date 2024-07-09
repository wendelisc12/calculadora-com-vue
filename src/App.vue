<script setup>
import { reactive } from "vue";
import resultado from "./components/resultado.vue";


const values = reactive({
  primeiroNumero: 0,
  segundoNumero: 0,
  operacao: 'adicao',
  resultado: 0
})

function calcular(){
  if(values.operacao === "adicao"){
    values.resultado = values.primeiroNumero + values.segundoNumero
  }else if(values.operacao === "subtracao"){
    values.resultado = values.primeiroNumero - values.segundoNumero
  }else if(values.operacao === "multiplicacao"){
    values.resultado = values.primeiroNumero * values.segundoNumero
  }else if(values.operacao === "divisao"){
    values.resultado = values.primeiroNumero / values.segundoNumero
  }
}

function escolha(op, e){
  if(op === "primeiro"){
    if(e.target.value === ''){
      values.primeiroNumero = 0
    }else{
      values.primeiroNumero = parseInt(e.target.value)
    }
    calcular()
  }else if(op === "segundo"){
    if(e.target.value === ''){
      values.segundoNumero = 0
    }else{
      values.segundoNumero = parseInt(e.target.value)
    }
    calcular()
  }else if(op === "operacao"){
    values.operacao = e.target.value
    calcular()
  }
}


</script>

<template>
  <div class="container">
    <div class="text-center mt-5">
      <h1>Calculadora</h1>
    </div>

    <div class="d-flex flex-column mt-4 align-items-center gap-3">
      <input type="number" class="w-25 form-control" @input="(e) => escolha('primeiro', e)" placeholder="Digite um número">
      <input type="number" class="w-25 form-control" @input="(e) => escolha('segundo', e)" placeholder="Digite um número">
      <select class="w-25 form-control" @change="(e) => escolha('operacao', e)" id="">
        <option value="adicao">Adição</option>
        <option value="subtracao">Subtração</option>
        <option value="multiplicacao">Multiplicação</option>
        <option value="divisao">Divisão</option>
      </select>
    </div>

    <div class="d-flex justify-content-center mt-4">
      <resultado :resultado="values.resultado" />
    </div>
  </div>
</template>

<style scoped>

</style>
