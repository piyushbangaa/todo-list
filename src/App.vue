<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <div class="max-w-md w-full p-4 bg-white rounded-xl shadow">
      <h1 class="text-2xl font-bold text-center mb-4">Vue To-Do List</h1>

      <TodoInput @add-task="addTask" />

      <TodoList
        :tasks="tasks"
        @toggle-complete="toggleComplete"
        @delete-task="deleteTask"
      />
    </div>
  </div>
</template>

<script>
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'App',
  components: {
    TodoInput,
    TodoList,
    TodoItem,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(task) {
      this.tasks.push({
        text: task,
        completed: false,
      });
    },
    toggleComplete(task) {
      task.completed = !task.completed;
    },
    deleteTask(task) {
      this.tasks = this.tasks.filter((t) => t !== task);
    },
  },
};
</script>