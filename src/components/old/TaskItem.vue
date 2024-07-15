<script setup>
import { ref } from 'vue';
import TaskEditModal from './TaskEditModal.vue'

defineProps({
    id: String,
    task: String, 
    createdAt: String,
    status: String 
})

const showEditModal = () => {
  editTaskModal.value.openModal();
}

const editTaskModal = ref(null)

// export default {
//     name: 'TaskItem',
//     props: props,
//     components: {
//         TaskEditModal,
//     },
//     methods: {
//         showEditModal() {
//             this.$refs.editTaskModal.openModal()
//         },
//     },
// }
</script>

<template>
    <div class="taskItem rounded w-100 mb-2 d-flex align-items-center justify-content-between">
        <div class="form-check">
            <input class="form-check-input" type="checkbox" value="" id="">
            <span class="text-start">{{ task }}</span>
        </div>
        <div class="d-flex gap-1">
            <button class="btn btn-outline-warning" @click="showEditModal" title="Edit Task">🏗️</button>
            <TaskEditModal ref="editTaskModal" />
            <button class="btn btn-outline-danger" title="Remove Task">🗑️</button>
        </div>
    </div>
</template>


<style scoped>
.taskItem {
    padding: 1rem 0.5rem;
    border: 1px solid transparent;
    transition: border 0.3s ease, background-color 0.3s ease;
}

.taskItem:hover {
    border: 1px solid var(--indigo);
    background-color: var(--black-mute);
}
</style>