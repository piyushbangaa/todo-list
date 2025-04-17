<template>
    <div class="mt-4 max-h-72 overflow-y-auto pr-2">
      <TodoItem
        v-for="(task, index) in tasks"
        :key="index"
        :task="task"
        @toggle-complete="$emit('toggle-complete', task)"
        @delete-task="$emit('delete-task', task)"
      />
    </div>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue';
  
  export default {
    components: {
      TodoItem,
    },
    props: {
      tasks: Array,
    },
  };
  </script>
  
  <style scoped>
  /* Any styling if needed */
  </style>
  