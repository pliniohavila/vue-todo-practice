<script>

export default {
    name: 'TaskEditModal',
    data() {
        return {
            taskName: '',
            taskStatus: '',
            showModal: false,
        };
    },
    methods: {
        setStatus(status) {
            this.taskStatus = status;
        },
        saveTask() {
            console.log(`Task Name: ${this.taskName}, Task Status: ${this.taskStatus}`);
            this.closeModal();
        },
        closeModal() {
            this.showModal = false;
        },
        openModal() {
            this.showModal = true;
        },
    },
};
</script>

<template>
    <div v-if="showModal" class="modal d-block" tabindex="-1">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="taskEditModalLabel">Edit Task</h5>
                </div>
                <div class="modal-body">
                    <div class="form-group mb-2">
                        <input type="text" class="form-control" id="taskName" v-model="taskName">
                    </div>
                    <!-- <div class="d-flex justify-content-between">
                        <button type="button" class="btn btn-warning"
                            @click="setStatus('Pending')">Pending</button>
                        <button type="button" class="btn btn-outline-success"
                            @click="setStatus('Completed')">Completed</button>
                    </div> -->
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" @click="closeModal">Close</button>
                    <button type="button" class="btn btn-primary" @click="saveTask">Save changes</button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.modal {
    display: block;
    background: rgba(0, 0, 0, 0.5);
}

.modal-content {
    border-radius: 10px;
    border: 1px solid var(--indigo);
}

.modal-title {
    font-size: 1.5rem;
    color: var(--indigo);
}

.form-control {
    border-radius: 10px;
    border: 1px solid var(--indigo);
    font-size: 1.5rem;
    color: var(--indigo);
}

.btn-outline-primary {
    border-radius: 10px;
    border: 1px solid var(--indigo);
    color: var(--indigo);
}

.btn-outline-primary:hover {
    background-color: var(--indigo);
    color: white;
}
</style>