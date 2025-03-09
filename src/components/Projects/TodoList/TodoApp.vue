<script setup>
  import { ref,watch, onMounted } from 'vue';

  const newTask = ref('')
  const tasks = ref([])

  const addTask = () => {
    if(newTask.value.trim() !== ''){
      tasks.value.push(newTask.value)
      newTask.value = ''
    }
  }

  const removeTask = (index) => {
    tasks.value.splice(index, 1)
  }

  const loadTasks = () => {
    const savedTasks = localStorage.getItem('tasks')
    if(savedTasks){
      tasks.value = JSON.parse(savedTasks)
    }
  }

  watch(tasks, (newTasks) =>{
      localStorage.setItem('tasks', JSON.stringify(newTasks))
    }, {deep: true})
    
  onMounted(loadTasks)

  
</script>

<template>
  <div class="flex flex-col justify-center items-center h-screen">
    <div class="glass p-5">
      <div class="flex flex-row justify-center items-center gap-4">
        <input v-model="newTask" placeholder="Add task..." @keyup.enter="addTask" class="border border-green-500 w-2xs outline-none p-2">
        <button @click="addTask" class="btn bg-green-500 border-none border-radius-none">Add</button>
      </div>

      <div class="flex flex-col items-center justify-center">
        <div 
        v-for="(task, index) in tasks" :key="index"
        class="grid grid-cols-[15px_288px_30px] gap-4 p-4">
          <input type="checkbox" class="" />
          <div class="">{{ task }}</div>
          <a @click="removeTask(index)" class=" flex items-center justify-center cursor-pointer">❌</a>
        </div>
      </div>

    </div>
  </div>
</template>