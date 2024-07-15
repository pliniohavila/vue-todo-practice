<script>
export default {
    data() {
        return {
            task: '',
        }
    },
    methods: {
        saveTask() {
            if (this.task) {
                let tasks = JSON.parse(localStorage.getItem('task')) || []
                const newTask = {
                    id: `${Date.now()}`,
                    task: this.task,
                    createdAt: new Date().toISOString(),
                    status: 'pending'
                }
                localStorage.setItem('task', JSON.stringify([...tasks, newTask]))
                this.task = ''
            }
        },
    },
}
</script>

<template>
    <div class="input-group">
        <input type="text" class="form-control" placeholder="New Task" v-model="task" />
        <button class="btn btn-outline-secondary" type="button" @click="saveTask">
            New Task
        </button>
    </div>
</template>

<style scoped></style>