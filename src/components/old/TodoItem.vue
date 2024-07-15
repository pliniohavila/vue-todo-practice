<script setup>

import DeleteTodoItem from './icons/DeleteTodoItem.vue'

const props = defineProps({
    id: Number
})
const emit = defineEmits(['deleteTodo', 'markTodo'])

const deleteTodo = () => emit('deleteTodo', props.id)
const completedTodo = () => emit('markTodo', props.id)

</script>
<template>
    <div class="task-list-body card p-2 mb-2">
            <div class="d-flex flex-row align-items-center justify-content-between">
                <div class="form-check align-items-baseline">
                    <input class="form-check-input" type="checkbox" name="marked"
                        @change="completedTodo"/>
                    <label class="form-check-label" for="marked">
                        <slot></slot>
                    </label>
                </div>
                <DeleteTodoItem 
                    class="delete" 
                    width="20" height="20" 
                    @click="deleteTodo"
                />
            </div>
        </div>
</template>

<style scoped>

.delete {
    cursor: pointer;
}

</style>