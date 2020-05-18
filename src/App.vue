<template>
  <div id="app">
    <Tasks :title="title" :tasks="tasks" @delete:task="deleteTask" />
  </div>
</template>

<script>
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: {
    Tasks
  },
  data: function() {
    return {
      title: 'Tasks for the day',
      tasks:
      [
        {
          id: 1,
          name: 'Study',
          completed: true,
        },
        {
          id: 2,
          name: 'Watch webseries',
          completed: false,
        },
        {
          id: 3,
          name: 'Create a todo app in vue js',
          completed: false,
        },
      ],
    }
  },
  methods: {
    deleteTask: function (id) {
        this.tasks = this.tasks.filter(
          task => task.id !== id
        )
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
