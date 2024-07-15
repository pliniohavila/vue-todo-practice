<script setup>
import { ref } from 'vue';

const newTodoInput = ref('')
const emit = defineEmits(['newTodo'])

const saveTodo = () => {
    emit('newTodo', newTodoInput.value)
    newTodoInput.value = ''
}

</script>

<template>
    <header class="w-50 mb-2 pt-5">
        <div class="title d-flex flex-row align-items-baseline justify-content-center">
            <img alt="Vue logo" class="m-2" src="../assets/logo.svg" width="30" height="30" />
            <h1>TODO</h1>
        </div>
        <form class="input-group mt-3 mb-3" @submit.prevent="saveTodo"
            >
            <input 
                type="text" 
                class="form-control" 
                placeholder="Adicione uma nova tarefa" 
                v-model="newTodoInput"    
            />
            <button 
                type="submit"
                class="btn btn-outline-secondary" 
                id="button-addon2"
                :disabled="newTodoInput.length < 2">
                    Criar
                </button>
        </form>
    </header>
</template>