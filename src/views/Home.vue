<template>
    <div>
        <h1>name in store is {{ name }}</h1>
        <input
            type="text"
            placeholder="new name"
            v-model="newName"
            name=""
            id=""
            class="border"
        />
        <button @click="saveName" class="bg-indigo-500 text-white">
            Change name
        </button>
    </div>
</template>

<script setup>
import { computed, ref } from 'vue'
import { useStore } from 'vuex'
const store = useStore()

import { useRouter } from 'vue-router'
const router = useRouter()

const name = computed(() => {
    return store.state.user.name
})

const newName = ref('')
const saveName = () => {
    store.dispatch('setName', newName.value)
    newName.value = ''
    router.push('/about')
}
</script>

<style></style>
