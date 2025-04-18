<template>
    <div class="flex items-center justify-between p-2 mb-2 bg-neutral-700/60 backdrop-blur-md rounded-lg w-full h-12 ">
      <div class="flex items-center">
        <input 
        type="checkbox"
        :checked="task.completed"
        @change="$emit('toggle-complete', task)"
  class="mr-2 w-6 h-6 appearance-none rounded-full border border-indigo-500 
         checked:bg-indigo-500  focus:outline-none 
         focus:ring focus:ring-indigo-400 transition"
 />

        <span :class="{'line-through text-gray-500': task.completed}" class="flex-1">
          {{ task.text }}
        </span>
      </div>
      <button
  @click="$emit('delete-task', task)"
  class="text-red-500 hover:text-red-700"
>
  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
    <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
    <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
  </svg>
</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      task: Object,
    },
  };
  </script>
  