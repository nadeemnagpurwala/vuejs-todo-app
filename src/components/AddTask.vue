<template>
    <div>
        <h1>{{ title }}</h1>
        <form @submit.prevent="addTask">
            <input type="text" class="form-control" v-model="name" placeholder="Name of the task">
            <input type="hidden" v-model="id">
            <input type="submit" class="btn btn-success" value="Save">
        </form>
    </div>
</template>

<script>
export default {
    name:"AddTask",
    props: {
        title: String,
    },
    data: function() {
        return {
            name: '',
            id: '4'
        }
    },
    methods: {
        addTask: function () {
            if(this.name === ''){
                return false
            }
            const newTask = {
                id : this.id++,
                name : this.name,
                completed : false
            }
            //Send to parent component
            this.$emit('add:task', newTask)
            this.name = ""
        }
    }
}
</script>

<style scoped>
    .btn-success {
        background-color: #28a745;
        border-color: #28a745;
    }
    div {
        text-align: center;
    }
</style>