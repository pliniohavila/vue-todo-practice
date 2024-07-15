<script setup>
import { ref } from 'vue'
import CoffeePlan from './CoffeePlan.vue'

const plans = ref(['The Single', 'The Curious', 'The Addict', 'The Hacker'])

const selectedCoffeePlan = ref('')

const handleSelectCoffeePlan = (name) => {
    selectedCoffeePlan.value = name
}

</script>

<template>
    <div class="plans card w-100 p-2">
        <div class="card mb-3">
            <div class="card-header">Coffee Plan Selected</div>
            <div class="card-body">
                {{ selectedCoffeePlan }}
            </div>
        </div>
        <CoffeePlan v-for="plan in plans" 
            :key="plan" 
            :name="plan" 
            :selected="plan == selectedCoffeePlan"
            @selected="handleSelectCoffeePlan"
        />
    </div>
</template>