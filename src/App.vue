<script setup>
import { ref } from 'vue';
import dynamicprops from './components/props/dynamicprops.vue';
const firstname = ref('Cedirc');
const lastname = ref('Belisario');
import staticprops from './components/props/staticprops.vue';
import propsValidation from './components/props/propsValidation.vue';
import arrayObjectProps from './components/props/arrayObjectProps.vue';
import CustomValidator from './components/props/CustomValidator.vue';

</script>

<template>
  <h1 class="text-red-500 font-bold">Static Props</h1>
  <staticprops  name="John" />
  <hr>
  
  <h1 class="text-blue-500 font-bold">Dynamic Props</h1>
  <dynamicprops :firstname="firstname" :lastname="lastname" />
  <button @click="firstname = 'John'" class="p-1 border m-1">Change firstname</button>
  <button @click="lastname = 'Doe'" class="p-1 border m-1">Change lastname</button>
  <hr>

  <h1 class="text-green-500 font-bold">Props Validation</h1>
  <propsValidation fullname='cedric' :age='21' />
  <hr>

  <h1 class="text-blue-500 font-bold">Complex Props</h1>
  <arrayObjectProps 
  :names="['cedric', 'kyle', 'belisario']" 
  :userInfo="{age: 21, email: 'cedric@gmail.com', address: ['Manabo', 'Abra']}"
  />
  <hr>

  <customValidator first-name="cedric" :age="21" password="12345678" />
</template> 

