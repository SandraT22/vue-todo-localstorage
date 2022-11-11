# ref = how you handle state. mounted = used for when we first render the page or the component, we call on this to get our local storage out of local storage. computed = created an ordered list our of our array. watch = will watch for any changes in our references (ref) to update local storage.

<script setup>
import { ref, onMounted, computed, watch } from 'vue'

# create references
const todos = ref([])
const name = ref('')

const input_content = ref('')
const input_category = ref(null)

const todos_asc = computed(() => todos.value.sort((a,b)) => {
    return b.createdAt - a.createdAt
}))

watch(name, (newVal) => {
    localStorage.setItem('name', newVal)
})

onMounted(() => {
    name.value = localStorage.getItem('name') || ''
})
</script>

<template>
 

    <main class ="app">

        <section class="greeting">
          <h2 class="title">
            What's up, <input type="text" placeholder="Name Here" v-model="name" />
          </h2>
</template>


