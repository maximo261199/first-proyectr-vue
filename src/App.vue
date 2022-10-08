//logica
<script setup>
  import { computed } from "@vue/reactivity";
import {onMounted, ref} from "vue";
  const name = "Vue dinamico";
 
  const counter = ref(0);
  const increment = () =>{
    counter.value++;
  }

/*
  const disminuir = computed(()=>{
    counter.value--;
    arrayFavorityNumber.forEach(element => {
        if (element === counter.value) valor= false;
        else valor= true;
      });
  
  })*/
 
  const disminuir =() =>{
    counter.value--;
    
  }


  const reiniciar =() =>{
    counter.value=0;
  }

  
  const bloaquearBtAdd = computed(()=>{
    const numSearch = arrayFavorityNumber.value.find(num => num === counter.value)
    return numSearch ? true: false;
  })

  const classCounter = computed(()=>{
      if (counter.value === 0) return "zero";
      else if (counter.value > 0) return "positive";
      else return "negative";
  })

 



  const add =(number)=>{
    


    arrayFavorityNumber.value.push(number);
    console.log("si se guardo");

  }

  const arrayFavorityNumber  = ref([])
 
 onMounted(() => console.log(arrayFavorityNumber.value))
</script>

//estructura
<template>
  <h1>Hola {{name.toUpperCase()  }}</h1>
  <h2 :class="classCounter">{{counter}}</h2>
  <button @click="increment">Aumentar</button>
  <button @click="disminuir">Disminuir</button>
  <button @click="reiniciar"> Reiniciar</button>
  <button @click="add(counter)" :disabled="bloaquearBtAdd" >Agregar</button>

  <ul>
    <li
      v-for="number in arrayFavorityNumber"
    >
       {{number}}
    </li>
  </ul>
</template>

//estilos
<style>
  h1{
    color: yellowgreen;
  }

  .positive{
    color: green;
  }

  .negative{
    color: red;
  }

  .zero{
    color:peru;
  }

  
</style>