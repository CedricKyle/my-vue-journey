<script setup>
import ListItems from './components/props&emit/ListItems.vue';
import { ref } from 'vue';

const cardItems = ref([
  {
    name:'Cedric',
    department:'IT',
    age:20,
    position:0
  },
  {
    name:'Kyle',
    department:'HR',
    age:25,
    position:1
  },
  {
    name:'John',
    department:'IT',
    age:20,
    position:2
  }
])

const deleteItem = (index) => {
  cardItems.value.splice(index, 1);
  
  //reset the position of the remaining items
  cardItems.value.forEach((ListItems, i) =>{
    ListItems.position = i;
  }) 

}
</script>

<template>
  <ListItems :cardItems="cardItems" @deleteItem="deleteItem" />
</template> 

