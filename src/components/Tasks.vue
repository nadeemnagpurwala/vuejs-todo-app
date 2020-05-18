<template>
    <div>
        <h1>{{ title }}</h1>
        <table>
            <tr>
                <th>Change Status</th>
                <th>Name</th>
                <th>Completed</th>
                <th>Action</th>
            </tr>
            <tr v-for="task in tasks" :key="task.id" :class="{ 'is-completed': task.completed }">
                <td><input type="checkbox" @click="updateTask(task)" :checked="task.completed"></td>
                <td>{{ task.name }}</td>
                <td v-if=task.completed>Yes</td> <td v-else>No</td>
                <td><button class="btn-danger" @click="$emit('delete:task', task.id)">Delete</button></td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    name:"Tasks",
    props: {
        title: String,
        tasks: Array,
    },
    methods: {
        updateTask: function (task) {
            console.log(task.completed)
            task.completed = !task.completed
        }
    }
}
</script>

<style scoped>
table {
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

.is-completed {
    background-color: #41b883;
    color: #fff;
}

.btn-danger {
    background-color: #dc3545;
    border-color: #dc3545;
    color: #fff;
    border: 1px solid transparent;
    height: 30px;
}
</style>