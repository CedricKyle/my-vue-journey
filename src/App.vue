<script setup>
import { ref } from 'vue';
import dynamicprops from './components/props/dynamicprops.vue';
const firstname = ref('Cedirc');
const lastname = ref('Belisario');
import staticprops from './components/props/staticprops.vue';
import propsValidation from './components/props/propsValidation.vue';
import arrayObjectProps from './components/props/arrayObjectProps.vue';


</script>

<template>
  <h1>Static Props</h1>
  <staticprops  name="John" />
  <hr>
  
  <h1>Dynamic Props</h1>
  <dynamicprops :firstname="firstname" :lastname="lastname" />
  <button @click="firstname = 'John'" class="p-1 border m-1">Change firstname</button>
  <button @click="lastname = 'Doe'" class="p-1 border m-1">Change lastname</button>
  <hr>

  <h1>Props Validation</h1>
  <propsValidation fullname='cedric' :age='21' />
  <hr>

  <h1>Complex Props</h1>
  <arrayObjectProps 
  :names="['cedric', 'kyle', 'belisario']" 
  :userInfo="{age: 21, email: 'cedric@gmail.com', address: ['Manabo', 'Abra']}"
  />
</template> 

