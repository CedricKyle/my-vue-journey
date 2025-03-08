<script setup>
import { ref } from 'vue';

 const textColor = ref('text-green-500')

 const updateTextColor = () =>{
  textColor.value = textColor.value === 'text-green-500' ? 'text-red-500' : 'text-green-500'
 }
                       
</script>

<template>
  <div class="flex justify-center items-center min-h-screen">
    <h1 v-bounce class="m-2" :class="textColor">Bounce Ako tol!</h1>
    <button v-bounce @click="updateTextColor"
    class="btn btn-primary">Bounce din ako tol!</button>
  </div>
</template>