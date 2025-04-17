<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <div class="max-w-md p-4 bg-white rounded-xl shadow">
      <h1 class="text-xl font-bold text-center mb-4">Vue To-Do List</h1>

      <TodoInput @add-task="addTask" />

      <div class="mt-4">
        <TodoItem
          v-for="(task, index) in tasks"
          :key="index"
          :task="task"
          @toggle-complete="toggleComplete"
          @delete-task="deleteTask"
        />
      </div>
    </div>
  </div>
</template>

<script>
import TodoInput from './components/TodoInput.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'App',
  components: {
    TodoInput,
    TodoItem,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(taskText) {
      this.tasks.push({ text: taskText, completed: false });
    },
    toggleComplete(task) {
      task.completed = !task.completed;
    },
    deleteTask(task) {
      this.tasks = this.tasks.filter(t => t !== task);
    },
  },
};
</script>

