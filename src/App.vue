<script setup>
import EventComponent from './components/EventComponent.vue';
import { ref } from 'vue';

const count = ref(0);

const handleSubmit = (username, email, password) => {
  console.log('username: ', username);
  console.log('email: ', email);
  console.log('password: ', password);
}
</script>

<template>
  
  <p>Count: {{ count }}</p>
  <EventComponent @increase-by="count++" @decrease-by="count--" @submit-form="handleSubmit" />
</template> 

