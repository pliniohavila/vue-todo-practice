<script setup>

import { ref } from 'vue'
import DeleteTodoItem from './icons/DeleteTodoItem.vue'

const props = defineProps({
    id: Number
})
const emit = defineEmits(['hasCompleted', 'toDelete'])

const isMarked = ref(false)

const markHasCompleted = () => {
    emit('hasCompleted', props.id)
}
const toDelete = () => {
    emit('toDelete', props.id)
}

</script>

<template>
    <div class="task-list-body card p-2 mb-2">
        <div class="d-flex flex-row align-items-center justify-content-between">
            <div class="form-check align-items-baseline">
                <input class="form-check-input" id="marked" type="checkbox" v-model="isMarked"
                    @change="markHasCompleted" />
                <label class="form-check-label" for="marked" :class="{ 'text-decoration-line-through': isMarked }">
                    <slot></slot>
                </label>
            </div>
            <DeleteTodoItem class="delete" width="20" height="20" @click="toDelete" />
        </div>
    </div>
</template>

<style scoped>
input[type="checkbox"],
.delete {
    cursor: pointer;
}
</style>