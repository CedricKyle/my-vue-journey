<script setup>
import LifeCycleHooks from './components/LifeCycleHooks.vue';
import { ref } from 'vue';

const show = ref(true);

const remove = () => {
  show.value = false;
}
</script>

<template>
  <LifeCycleHooks v-if="show" />
  <button @click="remove" class="p-1 bg-red-500 m-1 text-white">Remove</button>
</template> 

