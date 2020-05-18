<template>
  <div id="app">
    <AddTask @add:task="addTask" :title="titleAdd"/>
    <br>
    <Tasks :title="titleList" :tasks="tasks" @delete:task="deleteTask" />
  </div>
</template>

<script>
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Tasks,
    AddTask
  },
  data: function() {
    return {
      titleAdd: 'Add new task',
      titleList: 'Tasks for the day',
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
    },
    addTask: function (newTask) {
        this.tasks = [...this.tasks, newTask]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 30px;
}

h1 {
    text-align: center;
}

.btn {
  display: inline-block;
  border: none;
  padding: 6px 12px;
  cursor: pointer;
  color: #fff;
  text-align: center;
  font-size: 14px;
  border-radius: 4px;
}

.form-control {
  display: inline-block;
  width: 25%;
  padding: 6px 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 14px;
}
</style>
