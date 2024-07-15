<script setup>
// import {ref} from 'vue'

const props = defineProps({
    name: { 
        type: String, 
        default: 'Default Plan', 
        validator(value) {
            return value.startsWith("The")
        }
    },
    selected: { type: Boolean, default: false }
})

const emit = defineEmits({
    selected(payload) {
        return typeof payload == 'string'
    }
})

const selectPlan = () => {
    emit('selected', props.name)
}

</script>

<template>
    <div @click="selectPlan" 
        class="card description mb-1 p-2" 
        :class="{ 'bg-info': selected }"
        >
            <span class="title">
                {{ name }}
            </span>
    </div>
</template>

<style scoped>

.title {
    cursor: pointer
}

</style>