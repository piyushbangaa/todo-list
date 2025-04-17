<template>
    <div class="flex items-center justify-between p-2 mb-2 bg-gray-200 rounded-lg">
      <div class="flex items-center">
        <input
          type="checkbox"
          :checked="task.completed"
          @change="$emit('toggle-complete', task)"
          class="mr-2"
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
  