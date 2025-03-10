<script setup>
import { Delete } from 'lucide-vue-next';
import {ref} from 'vue';

const display = ref('')

const handleClick = (input) => {
  display.value += input
}

const allClear = () => {
  display.value = ''
}

const calculate = () => {
  try{
    display.value = eval(display.value)
  }catch(e){
    display.value = 'Error: Invalid expression'
  }
}

const deleteValue = () => {
  const length = display.value.length
  display.value = display.value.slice(0, length - 1)
}

</script>

<template>
  <div class="flex justify-center items-center min-h-screen">
    <div class=" border calculator-container h-120 w-70 p-5">
      <div class="flex justify-center">
          <input 
          class=" text-right p-2 w-[100%] h-20 text-2xl"
          readonly placeholder="0" v-model="display">
      </div>
      <div class="border h-[80%]">
        <div class="grid grid-cols-[80%_20%]">
          <div class="first-container grid grid-cols-3">
            <button @click="allClear">Ac</button>
            <button @click="deleteValue" class="flex justify-center items-center"><Delete class="" /></button>
            <button @click="handleClick('/')">/</button>
            <button @click="handleClick(7)">7</button>
            <button @click="handleClick(8)">8</button>
            <button @click="handleClick(9)">9</button>
            <button @click="handleClick(4)">4</button>
            <button @click="handleClick(5)">5</button>
            <button @click="handleClick(6)">6</button>
            <button @click="handleClick(1)">1</button>
            <button @click="handleClick(2)">2</button>
            <button @click="handleClick(3)">3</button>
          </div>

          <div class="second-container grid grid-rows-[25%_25%_37.5%_37.5%] ">
            <button @click="handleClick('*')">*</button>
            <button @click="handleClick('-')">-</button>
            <button @click="handleClick('+')">+</button>
            <button @click="calculate">=</button>
          </div>

          <div class="third-container grid grid-cols-[66.5%_33.5%]">
          <button @click="handleClick(0)">0</button>
          <button @click="handleClick('.')">.</button>
        </div>
        </div>
    </div>
  </div>    
  </div>
</template>

<style>
button{
  border: solid 1px;
}
</style>