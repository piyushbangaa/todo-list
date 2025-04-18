<template>
  <div class="min-h-screen bg-neutral-800 flex items-center justify-center px-4">
    <div class="w-full max-w-md rounded-2xl bg-neutral-700/70 backdrop-blur-lg shadow-xl p-6 text-white h-130">
      <h1 class="text-3xl font-bold mb-1">Today's Tasks</h1>
      <p class="text-sm text-gray-300 mb-6">{{ today }}</p>

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
      today: new Date().toLocaleDateString('en-GB', {
        weekday: 'long',
        day: '2-digit',
        month: 'long',
        year: 'numeric',
      }),
    };
  },
  methods: {
    addTask(task) {
      console.log('Task added:', task);
      this.tasks.push({
        ...task,
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
