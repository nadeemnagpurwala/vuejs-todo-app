<template>
    <div>
        <h1>{{ title }}</h1>
        <table>
            <tr>
                <th>Name</th>
                <th>Completed</th>
            </tr>
            <tr v-for="task in tasks" :key="task.id">
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

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>