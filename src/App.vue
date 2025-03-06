<script setup>
import { ref } from 'vue';
import dynamicprops from './components/props/dynamicprops.vue';
const firstname = ref('Cedirc');
const lastname = ref('Kabongo');
import staticprops from './components/props/staticprops.vue';

</script>

<template>
  <staticprops  name="John" />
  <dynamicprops :firstname="firstname" :lastname="lastname" />
</template> 

