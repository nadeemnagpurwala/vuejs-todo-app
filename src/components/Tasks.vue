<template>
    <div>
        <h1>{{ title }}</h1>
        <table>
            <tr>
                <th>Mark Complete</th>
                <th>Id</th>
                <th>Name</th>
                <th>Completed</th>
                <th>Action</th>
            </tr>
            <tr v-for="task in tasks" :key="task.id" :class="{ 'is-completed': task.completed }">
                <td><input type="checkbox" @click="updateTaskStatus(task)" :checked="task.completed"></td>
                <td>{{ task.id }}</td>
                
                <td v-if="editMode === task.id">
                    <input type="text" class="form-control" v-model="task.name" placeholder="Name of the task">
                </td>
                <td v-else>{{ task.name }}</td>

                <td v-if=task.completed>Yes</td> <td v-else>No</td>

                <td v-if="editMode === task.id">
                    <button class="btn btn-success" @click="updateTask(task)">Save</button>
                    <button class="btn btn-default" @click="cancelEdit(task)">Cancel</button>
                </td>
                <td v-else>
                    <button class="btn btn-info" @click="setEditMode(task)">Edit</button>
                    <button class="btn btn-danger" @click="$emit('delete:task', task.id)">Delete</button>
                </td>
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
    data: function() {
        return {
            editMode: '',
            oldData: ''
        }
    },
    methods: {
        updateTaskStatus: function (task) {
            task.completed = !task.completed
        },
        setEditMode: function (task) {
            this.editMode = task.id
            this.oldData = JSON.parse(JSON.stringify(task))
        },
        updateTask: function (task) {
            if (task.name === '') {
                return false
            }
            //Send to parent component
            this.$emit('update:task', task.id, task)
            this.editMode = null
        },
        cancelEdit: function (task) {
            task.name = this.oldData.name
            this.editMode = null
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
}

.btn-info {
    background-color: #02a4e4;
    border-color: #02a4e4;
}

.btn-success {
    background-color: #28a745;
    border-color: #28a745;
}

.btn-default {
    background-color: #888181;
    border-color: #888181;
}

.form-control {
    width: 50%;
}
</style>