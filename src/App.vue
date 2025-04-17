<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <div class="max-w-md p-4 bg-white rounded-xl shadow">
      <h1 class="text-xl font-bold text-center mb-4">Vue To-Do List</h1>

      <TodoInput @add-task="addTask" />
    </div>
  </div>
</template>

<script>
import TodoInput from './components/TodoInput.vue';

export default {
  name: 'App',
  components: {
    TodoInput,
  },
  methods: {
    addTask(task) {
      console.log('Task added:', task);
    },
  },
};
</script>

