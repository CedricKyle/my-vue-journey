<script setup>
  import { ref } from 'vue';

  const searchQuery = ref('')
  const searchResults = ref([])
  const isLoading = ref(false)
  const error = ref(null)
  const theme = ref('dark')

  const searcWikipedia = async (query) => {
    const encodedQuery = encodeURIComponent(query);
    const endpoint = `https://en.wikipedia.org/w/api.php?action=query&list=search&prop=info&inprop=url&utf8=&format=json&origin=*&srlimit=10&srsearch=${encodedQuery}`
    isLoading.value = true
    try{
      
      const response = await fetch(endpoint);
      const data = await response.json();

      console.log(data) // check api data lng hehe
      if(data.query && data.query.search){
        searchResults.value = data.query.search;
        error.value = null
        isLoading.value = false
      }else{
        searchResults.value = [];
        error.value = 'No results found for the given query';
      }
    }catch(err){
      console.error(err);
      isLoading.value = false;
    }
  }

  // searcWikipedia()

  const submitSearch = () => {
    if(searchQuery.value.trim() !== ''){
      searcWikipedia(searchQuery.value);
    }else{
      searchResults.value = [];
      error.value = 'Please enter a search query';
    }
  }

  const toggleTheme = () => {
    theme.value = theme.value === 'light'? 'dark' : 'light';
    document.documentElement.setAttribute('data-theme', theme.value);
  }
</script>

<template>
  <div class="flexmin-h-screen items-center justify-center">
    <label class="theme-color flex cursor-pointer gap-2 fixed top-4 right-10">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="20"
        height="20"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round">
        <circle cx="12" cy="12" r="5" />
        <path
          d="M12 1v2M12 21v2M4.2 4.2l1.4 1.4M18.4 18.4l1.4 1.4M1 12h2M21 12h2M4.2 19.8l1.4-1.4M18.4 5.6l1.4-1.4" />
      </svg>
      <input type="checkbox" @change="toggleTheme" class="toggle theme-controller" />
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="20"
        height="20"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round">
        <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
      </svg>
    </label>

    <form @submit.prevent="submitSearch" class="text-center flex flex-col mt-6">
      <h1 class="text-5xl ">Wiki mo Pedia ko</h1>
      <div class="flex justify-center w-full gap-2 mt-6">
        <input v-model="searchQuery" 
        type="text" placeholder="search" class="input focus:outline-none">
        <button type="submit" class="btn">Search</button>
      </div>
    </form>

    <div class="results-container flex justify-center">
      <div v-if="isLoading" class="loading-page">
        <span class="loading loading-spinner loading-xs"></span>
      </div>
      <p v-if="error">{{ error }}</p>

      <div v-if="searchResults.length" class="">
        <div v-for="result in searchResults" :key="result.pageid" class="result-for-loop m-5 text-justify">
          <h2 class="title text-2xl">
            <a :href="`https://en.wikipedia.org/?curid=${result.pageid}`" target="_blank" rel="noopener">
              {{ result.title }}
            </a>
          </h2>
            <a class="text-blue-400" 
            :href="`https://en.wikipedia.org/?curid=${result.pageid}`" target="_blank" rel="noopener">
              {{ `https://en.wikipedia.org/?curid=${result.pageid}` }}
            </a>
            <p v-html="result.snippet"></p>
        </div>
      </div>
    </div>
  </div>
</template>