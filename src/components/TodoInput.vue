<template>
    <div class="mb-4 flex items-center">
      
      <input
        v-model="newTaskText"
        type="text"
        placeholder="Add a new task"
        class="flex-1 px-4 py-2 border border-gray-600 bg-neutral-700/60 backdrop-blur-md rounded-md focus:outline-none focus:ring-2 focus:ring-gray-500"
      />

      <button
        @click="addTask"
        class="px-4 py-2 ml-2 bg-blue-500 text-white rounded-xl hover:bg-blue-600 transition"
      >
        +
      </button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTaskText: '',
      };
    },
    methods: {
      addTask() {
        if (this.newTaskText.trim()) {
          this.$emit('add-task', { text: this.newTaskText });
          this.newTaskText = ''; 
        }
      },
    },
  };
  </script>
  