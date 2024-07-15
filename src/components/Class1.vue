<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
import { ref, computed } from 'vue';

const header = ref("Shopping List App")
const editing = ref(false)
const items = ref([
    { id: 1, label: 'Skirt', purchased: true, highPriority: false },
    { id: 5, label: 'T-shirt', purchased: false, highPriority: true },
    { id: 4, label: 'Hat', purchased: true, highPriority: true },
])

const newItem = ref("")
const newItemHighPriority = ref(false)
const characterCount = computed(() => {
    return newItem.value.length
})
// const reversedItems = computed(() => 
//     [...items.value].reverse()
// )
const saveItem = () => {
    items.value.push({
        id: items.value.length + 1,
        label: newItem.value,
        purchased: false,
        highPriority: newItemHighPriority.value
    })
    newItem.value = ''
    newItemHighPriority.value = ''
}

const doEdit = (e) => {
    editing.value = e
    newItem.value = ''
}

const togglePurchased = (item) => {
    item.purchased = !item.purchased
}
</script>

<template>
    <div class="header">
        <h1>{{ header }}</h1>
        <button v-if="editing" class="btn btn-secondary" @click="doEdit(false)">
            Cancel
        </button>
        <button v-else class="btn btn-primary" @click="doEdit(true)">
            Add Item
        </button>
    </div>
    <form class="add-item-form" v-if="editing" @submit.prevent="saveItem">
        <input v-model.trim="newItem" type="text" placeholder="add an item" />
        <label class="m-2">
            <input type="checkbox" v-model="newItemHighPriority" v-bind:disabled="newItem.length < 2" />
            High Priority
        </label>
        <button class="btn btn-primary" v-bind:disabled="newItem.length < 2">
            Save Item
        </button>

    </form>
    <p class="counter">
        {{ characterCount }}/200
    </p>
    <ul>
        <li v-for="item in items" 
            @click="togglePurchased(item)" 
            :key="item.id" 
            class="static-class" 
            :class="{
                strikeout: item.purchased,
                priority: item.highPriority
            }"
        >
            {{ item.label }}
        </li>
    </ul>
    <p v-if="!items.length">
        Nothing to see here
    </p>
    <!-- <pre>
            {{ items }}
        </pre> -->

</template>
