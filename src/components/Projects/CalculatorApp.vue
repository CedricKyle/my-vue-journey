<script setup>
import { Delete, Percent  } from 'lucide-vue-next';
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
    <div class="
    flex flex-col justify-center
    glass
    border calculator-container h-120 w-70 p-5 rounded-2xl">
      <div class="flex justify-center mt-10">
          <input 
          class=" text-right p-2 w-[80%]  text-[20px]  border rounded-sm"
          readonly placeholder="0" v-model="display">
      </div>
      <div class="flex justify-center p-3 h-[80%]">
          <div class="first-container grid grid-cols-4  gap-3 p-2">
            <button @click="allClear" class="text-green-500">Ac</button>
            <button @click="deleteValue" class="flex justify-center items-center text-green-500"><Delete class="text-green-500" /></button>
            <button @click="handleClick('%')" class="flex justify-center items-center text-green-500"><Percent class="text-green-500" /></button>
            <button @click="handleClick('/')" class="text-green-500">/</button>
            <button @click="handleClick(7)">7</button>
            <button @click="handleClick(8)">8</button>
            <button @click="handleClick(9)">9</button>
            <button @click="handleClick('*')" class="text-green-500">*</button>
            <button @click="handleClick(4)">4</button>
            <button @click="handleClick(5)">5</button>
            <button @click="handleClick(6)">6</button>
            <button @click="handleClick('-')" class="text-green-500">-</button>
            <button @click="handleClick(1)">1</button>
            <button @click="handleClick(2)">2</button>
            <button @click="handleClick(3)">3</button>
            <button @click="handleClick('+')" class="text-green-500">+</button>
            <button @click="handleClick('')">+/-</button>
            <button @click="handleClick(0)">0</button>
            <button @click="handleClick('.')">.</button>
            <button @click="calculate" class="text-green-500">=</button>
          </div>

        </div>
    </div>
  </div>    
</template>

<style scoped>
button{
  width: 40px;
  height: 40px;
  border: solid .5px;
  border-radius: 10px;
  font-size: 20px;
  cursor: pointer;
}
</style>