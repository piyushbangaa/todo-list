<template>
  <div class="min-h-screen bg-neutral-800 flex items-center justify-center px-4">
    <div class="w-140 rounded-2xl bg-neutral-700/70 backdrop-blur-lg shadow-xl p-6 text-white h-150 overflow-y-auto">
      <h1 class="text-4xl font-bold mb-1 opacity-90">Today's Tasks</h1>
      <p class="text-xl text-gray-300 mb-6">{{ today }}</p>

      <TodoInput @add-task="addTask" />

      <h2 class="text-2xl font-semibold mt-6 opacity-80">Active Tasks</h2>
      <div class="max-h-72 overflow-y-auto">
        <div v-if="activeTasks.length === 0" class="text-gray-400 text-center mt-3">
          There are no active tasks.
        </div>
        <TodoList
          v-else
          :tasks="activeTasks"
          @toggle-complete="toggleComplete"
          @delete-task="deleteTask"
        />
      </div>

      <h2 class="text-2xl font-semibold mt-4 opacity-80">Completed Tasks</h2>
      <div class="max-h-72 ">
        <TodoList
          :tasks="completedTasks"
          @toggle-complete="toggleComplete"
          @delete-task="deleteTask"
        />
      </div>
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
      tasks: this.loadTasks(),
      today: new Date().toLocaleDateString('en-GB', {
        weekday: 'long',
        day: '2-digit',
        month: 'long',
        year: 'numeric',
      }),
    };
  },
  computed: {
    activeTasks() {
      return this.tasks.filter(task => !task.completed);
    },
    completedTasks() {
      return this.tasks.filter(task => task.completed);
    }
  },
  methods: {
    loadTasks() {
      const tasks = JSON.parse(localStorage.getItem('tasks'));
      return tasks ? tasks : [];
    },

    saveTasks() {
      localStorage.setItem('tasks', JSON.stringify(this.tasks));
    },

    addTask(task) {
      this.tasks.push({
        ...task,
        completed: false,
      });
      this.saveTasks();
    },

    toggleComplete(task) {
      task.completed = !task.completed;
      this.saveTasks();
    },

    deleteTask(task) {
      this.tasks = this.tasks.filter(t => t !== task);
      this.saveTasks();
    },
  },
};
</script>
