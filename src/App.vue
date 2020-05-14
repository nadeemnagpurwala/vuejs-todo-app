<template>
  <div id="app">
    <Tasks :title="title" :tasks="tasks"/>
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
