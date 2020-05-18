<template>
    <div>
        <h1>{{ title }}</h1>
        <table>
            <tr>
                <th>Change Status</th>
                <th>Name</th>
                <th>Completed</th>
            </tr>
            <tr v-for="task in tasks" :key="task.id" :class="{ 'is-completed': task.completed }">
                <td><input type="checkbox" @click="changeStatus(task)" :checked="task.completed"></td>
                <td>{{ task.name }}</td>
                <td v-if=task.completed>Yes</td>
                <td v-else>No</td>
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
        changeStatus: function (task) {
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
</style>