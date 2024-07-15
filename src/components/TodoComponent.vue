<script setup>
import { ref, computed} from 'vue'
import TodoHeader from './TodoHeader.vue'
import TodoItem from './TodoItem.vue'

const todos = ref([
    {
        id: 42, 
        task: 'Maker launch',
        completed: false
    }, 
    {
        id: 4, 
        task: ' Create todo list itens html element',
        completed: false
    }, 
    {
        id: 21, 
        task: 'com.eventostec.api.domain.address.Address;',
        completed: false
    }, 
])

const created = computed(() => todos.value.length)
const completed = computed(() => 
    todos.value.filter((t) => 
        t.completed !== false)
        .length
)

const handleCompleted = (id) => todos.value.forEach((t) => {
    if (t.id === id)
        t.completed = ! t.completed
})
const handleDeleted = (id) => {
    todos.value = todos.value.filter((t) => t.id !== id)
}

const handleNewTodo = (newTodo) => {
    todos.value.push({
        id: Date.now(), 
        task: newTodo, 
        completed: false
    })
}

</script>
<template>
    <TodoHeader @newTodo="handleNewTodo"/>
    <main class="w-50">
        <div class="task-list-header d-flex justify-content-between">

            <div>
                <p class="fw-semibold">Tarefas Criadas 
                    <span class="badge rounded-pill text-bg-primary">{{ created }}</span>
                </p>
            </div>
            <div>
                <p class="fw-semibold">Concluídas 
                    <span class="badge rounded-pill text-bg-info">
                        {{ completed }} de {{ created }}
                    </span>
                </p>
            </div>
        </div>

        <TodoItem v-for="todo in todos" 
            :key="todo.id" 
            :id="todo.id" 
            @hasCompleted="handleCompleted"
            @toDelete = "handleDeleted"
        >
            {{ todo.task }}
        </TodoItem>
    </main>
</template>

<style scoped></style>
