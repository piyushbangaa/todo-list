<template>
    <div class="flex items-center justify-between p-2 mb-2 bg-neutral-700/60 backdrop-blur-md rounded-lg w-full h-12 ">
      <div class="flex items-center">
        <input 
        type="checkbox"
        :checked="task.completed"
        @change="$emit('toggle-complete', task)"
        class="mr-2 w-5 h-5 appearance-none rounded-full border border-indigo-500 
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
        Delete
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
  