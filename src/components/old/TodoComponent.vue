<script setup>

import { ref } from 'vue';
import TodoItem from './TodoItem.vue'
import HeaderTodo from './HeaderTodo.vue'

const todos = ref([
    {
        id: Date, 
        task: 'Make a new music using IA', 
        completed: false,
    },
    {
        id: 4, 
        task: 'Implement component TodoItem', 
        completed: false,
    }, 
    {
        id: 2, 
        task: 'Implement refs to var tasks created and tasks completed', 
        completed: false,
    },
    {
        id: 21, 
        task: 'Implement component that insert new todos', 
        completed: false,
    }
])

const todosCreated = ref(todos.value.length)
const todosCompleted = ref(
    todos.value.filter((t) => t.completed === true).length
)

const handleAddNewTodo = (newTodo) => {
    todos.value.push({
        id: Date.now(), 
        task: newTodo,
        completed: false
    })
    updateTodosCreated()
}

const handleMarkCompleted = (id) => {
    todos.value.forEach((td) => {
        if (td.id === id)
            td.completed = !td.completed
    })
    updateTodosCompleted()
}

const handleDelete = (id) => {
    todos.value = todos.value.filter((td) => td.id !== id)
    updateTodosCreated()
    updateTodosCompleted()
    
}

const updateTodosCreated = () => todosCreated.value = todos.value.length
const updateTodosCompleted = () => 
    todosCompleted.value = todos.value.filter((t) => t.completed === true).length

</script>
<template>
    <HeaderTodo @newTodo="handleAddNewTodo" />

    <main class="w-50">
        <div class="task-list-header d-flex justify-content-between">

            <div>
                <p class="fw-semibold">Tarefas Criadas 
                    <span class="badge rounded-pill text-bg-primary">{{ todosCreated }}</span>
                </p>
            </div>
            <div>
                <p class="fw-semibold">Concluídas 
                    <span class="badge rounded-pill text-bg-info">
                        {{ todosCompleted }} de {{ todosCreated }}</span>
                    </p>
            </div>

        </div>

        <TodoItem 
            v-for="todo in todos" 
            :key="todo.id"
            :id="todo.id"
            @deleteTodo="handleDelete"
            @markTodo="handleMarkCompleted"
        >
            {{ todo.task }}
        </TodoItem>
    </main>
</template>

<style scoped>
header {
    line-height: 3;
    height: 200px;
}

.delete {
    cursor: pointer;
}
</style>
