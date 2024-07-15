<script setup>
import { ref } from 'vue'

const todoInput = ref('')
const emit = defineEmits(['newTodo'])

const newTodoSubmit = () => {
    emit('newTodo', todoInput.value)
    todoInput.value = ''
}

</script>

<template>
    <header class="w-50 mb-2 pt-5">
        <div class="title d-flex flex-row align-items-baseline justify-content-center">
            <img alt="Vue logo" class="m-2" src="../assets/logo.svg" 
            width="30" height="30" />
            <h1>TODO</h1>
        </div>
        <form class="input-group mt-3 mb-3" @submit.prevent="newTodoSubmit">
            <input 
                type="text" 
                class="form-control" 
                placeholder="Adicione uma nova tarefa" 
                v-model="todoInput"/>
            <button 
                class="btn btn-outline-secondary" 
                type="submit">
                Criar
            </button>
        </form>
    </header>
</template>
<style scoped>
header {
    line-height: 3;
    height: 200px;
}
</style>