<template>
    <div class="mb-4">
      <input
        v-model="task"
        @keyup.enter="addTask"
        type="text"
        class="w-full px-4 py-2 border rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
        placeholder="Add a new task"
      />
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        task: '',
      };
    },
    methods: {
      addTask() {
        if (this.task.trim()) {
          this.$emit('add-task', this.task); 
          this.task = ''; 
        }
      },
    },
  };
  </script>
  