<script setup>
import { ref, computed } from 'vue'

import IconWarning from './icons/IconWarning.vue'
import IconInfo from './icons/IconInfo.vue'
import IconError from './icons/IconError.vue'

const props = defineProps({
    type: {String, default: 'primary'}
})

const emit = defineEmits(['closed'])


const alertType = computed(() => {
    return {
        info: 'alert-info',
        warning: 'alert-warning', 
        error: 'alert-danger', 
        success: 'alert-success'
    }[props.type]
})

const icon = computed(() => {
    return {
        info: IconInfo,
        warning: IconWarning, 
        error: IconError, 
        success: IconInfo
    }[props.type]
})

const closed = ref(false)
function close() {
    closed.value = true
    emit('closed')
}

</script>

<template>
    <div v-if="!closed" :class="`alert ${alertType}`" role="alert">
        <component :is="icon"></component>
        <span><slot></slot></span>
        <button class="btn btn-danger" @click="close">X</button>
    </div>
</template>