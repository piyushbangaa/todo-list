<template>
    <div class="mb-4 flex items-center">
      <!-- Input Field -->
      <input
        v-model="newTaskText"
        type="text"
        placeholder="Add a new task"
        class="flex-1 px-4 py-2 border border-gray-600 rounded-md focus:outline-none focus:ring-2 focus:ring-gray-500"
      />
      <!-- Add Button -->
      <button
        @click="addTask"
        class="px-4 py-2 ml-3 bg-blue-500 text-white rounded-xl hover:bg-blue-600 transition"
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
          this.newTaskText = ''; // Reset input field
        }
      },
    },
  };
  </script>
  