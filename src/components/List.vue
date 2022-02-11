<script setup>
import useTodos from "../composables/useTodos";

const { pending, completed, changeStatus } = useTodos();

defineProps({
isCompleted: {
default: false,
type: Boolean,
},
});

</script>

<template>
    
    
<div class="w-1/3">
<h3 class="text-4xl font-bold text-center"  :class="isCompleted ?  'text-yellow-600' : 'text-purple-300' ">{{ isCompleted ? 'Completed' : 'Pending' }}</h3>
<ul class="pt-8 space-y-4">
  <li 
  v-for="todo in isCompleted ? completed : pending "
  :key="todo.id"
  @click="changeStatus(todo.id)"
  :class="
  isCompleted 
  ? 'text-yellow-600  hover:bg-purple-300'
   :'text-purple-300  hover:bg-blue-400'"
  class= "w-full px-4 py-2 font-bold text-center bg-slate-400 bg duration-500 rounded-lg hover:cursor-pointer  hover:text-gray-200">

 {{ todo.content }}
  </li>
   
</ul>
</div>

</template>