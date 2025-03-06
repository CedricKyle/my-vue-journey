<script setup>
  defineProps({
    names: Array,
    userInfo: Object,
  });
</script>

<template>
  <h1>Names: {{ names[2] }}</h1>
  <h1>User Info: {{ userInfo.address[0] }}</h1>
  <br>

  <!-- Iterate Array -->
  <ul v-for="name in names" :key="name">
    <li>{{ name }}</li>
  </ul>

  <!--Iterate Object -->
  <ul v-for="(info, i) in userInfo" :key="i">
    <li>{{ info }}</li>
  </ul>

  <!-- <p>{{ userInfo.age }}</p> -->
</template>

