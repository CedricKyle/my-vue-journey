<script setup>
  const greet = 'Hello baby '
  const myNAME = 'Cedric Kyle'
  function add(x, y) {
    return x + y;
  }
</script>

<template>
  <h1 class="text-red-500">{{greet + myNAME }}</h1>
  <h2>2 + 2 = {{ add(2, 2) }}</h2>
</template>

<style scoped>
  @import "tailwindcss";
</style>