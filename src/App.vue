
<script setup>
import { ref,computed } from "vue";
const name = "viu es dinamioo este es el mejor vue es mejor ";
const azul = "color: blue"
const red = "color: red"
const green = "color:green"
const click = (mensaje) => {
  console.log(mensaje)
}

// anf = snippet de funcion flecha

const contar = ref(0);
const arrayFavoritos = ref([]);
const increment = () => {
  contar.value ++;
}
const disminuir = () => {
  contar.value --;
}
const resetear = () => {
  contar.value = 0;
}
const add = () => {
arrayFavoritos.value.push(contar.value)
}
const bloquearBoton = computed(() => {
  const numSear = arrayFavoritos.value.find(num => num === contar.value)
  console.log(numSear)
  // if(numSear === 0) return true;
  // return numSear ? true : false;
  return numSear || numSear === 0;
})
const compute = computed(() => { 
  if(contar.value === 0){
    return 'zero';
  }
  if(contar.value > 0 ){
    return 'positive';
  }
  if(contar.value < 0){
  return 'negative'
  }
 });
</script>
<template>
  <div class="container text-center mt-3">
  <h1>dime dime si has podido olvidarme</h1>
   <p>{{  name  }}</p>
   <h2 v-bind:style="azul" >soy azul</h2>
   <!-- puedes quitar el v-bind y solo poner los :  -->
   <h2 :style="azul" >soy azul</h2>
   <button v-on:click="click('este es samas')" class="btn btn-success">samas</button>
    <button v-on:click="click('este es broly')" class="btn btn-danger">broly</button>
   <button @click="click('este es jiren')" class="btn btn-secondary">jiren</button>
   
   <!-- <h2 v-if="contar > 0" :style="azul" > {{ contar }}</h2>
   <h2 v-if="contar < 0" :style="red" > {{ contar }}</h2>
   <h2 v-if="contar == 0" :style="green" > {{ contar }}</h2>
 -->
   <h2 :class="compute"> {{ contar }}</h2>

   <div class="btn-group">

     <button @click="increment" class="btn btn-warning" >Aumentar</button>
     <button @click="disminuir" class="btn btn-info">disminuir</button>
     <button @click="resetear" class="btn btn-light">resetear</button>
     <button @click="add" :disabled="bloquearBoton" class="btn btn-success">Add</button>
    </div>
   <br />
   {{ arrayFavoritos }}
   <ul>
    <li v-for="(num, index) in arrayFavoritos" :key="index">
       {{ num }}
    </li>
   </ul>
  </div>
</template>
<style>
h1{
  color: yellow;
}
.positive{
  color: red;
}
.negative{
  color: green;
}
.zero{
  color: rgb(95, 12, 237);
}
</style>