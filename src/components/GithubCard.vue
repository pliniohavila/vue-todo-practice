<script setup>
import {ref} from 'vue'

const props = defineProps({
    username: { type: String, required: true}
})

const user = ref('')

fetch(`https://api.github.com/users/${props.username}`)
    .then(async (rest) => {
        const data = await rest.json()
        user.value = data

        console.log(data)
    })

</script>
<template>
    <div class="card text-dark bg-info mb-3" v-if="user" style="max-width: 18rem;">
        <img class="card-img-top" :src="user.avatar_url" />
        <div class="card-body">
            <div class="card-title">
                <h3><b>{{ user.name }}</b></h3>
            </div>
            <p>
                Followers: {{ user.followers }}
            </p>
            <p>
                Following: {{ user.following }}
            </p>
            <a :href="user.html_url" target="_blank" class="btn btn-primary" rel="noopener noreferrer">
                @{{ user.login }}
            </a>
               
        </div>
    </div>
</template>