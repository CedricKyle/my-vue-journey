<script setup>
  import { ref, onMounted } from 'vue';

  const user = ref([])
  const loading = ref(true)
  const error = ref(null)

  const fetchUsers = async () => {
    try{
      const response = await fetch('https://jsonplaceholder.typicode.com/users')
      if(!response.ok){
      throw new Error('Error fetching data')
      }

      user.value = await response.json()

      setTimeout(()=> {
      loading.value = false
    },2000)

    }catch(e){
      error.value = e.message
      loading.value = false
    }
  }

  onMounted(fetchUsers)
</script>

<template>
  <div class="flex flex-col justify-center items-center min-h-full p-4">
    <p class="font-bold text-4xl">User List</p>
    <p v-if="loading">Loading...</p>
    <p v-if="error" class="text-red-500">{{ error }}</p>
      
    <ul v-if="!loading && !error">
      <li v-for="users in user" :key="users.id" class="p-2 border">
        <p>Name: {{ users.name }}</p>
        <p>Email:{{ users.email }}</p>
      </li>
    </ul>
  </div>
</template>