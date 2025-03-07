<script setup>
import SchoolComponent from './components/provide and inject/SchoolComponent.vue';
import { provide } from 'vue';

const studentInfo = {
  name:'Cedric Kyle D. Belisario',
  age:20,
  course:'BSIT'
}

provide('schoolInfo', ['NCST', 'CIT-U', 'STI']) 

const games = [
  {
    title: 'Space Explorer',
    genre: 'Sci-Fi',
    platform: 'PC',
    releaseDate: '2023-05-20'
  },
  {
    title: 'Fantasy Quest',
    genre: 'Fantasy',
    platform: 'PlayStation',
    releaseDate: '2023-07-10'
  },
  {
    title: 'Inception',
    director: 'Christopher Nolan',
    genre: 'Sci-Fi',
    releaseDate: '2010-07-16'
  },
  {
    title: 'The Shawshank Redemption',
    director: 'Frank Darabont',
    genre: 'Drama',
    releaseDate: '1994-09-23'
  }
]

provide('studentInfo', studentInfo);
provide('games', games);
</script>

<template>
  <SchoolComponent />
</template> 

