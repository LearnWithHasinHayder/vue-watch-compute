<script setup>
import { ref, watch, onBeforeMount, watchEffect } from 'vue'

const postId = ref(1)
const post = ref({});

const postIds = ref([1])

watch(postId, (newValue, oldValue) => {
    console.log(`Post ID changed from ${oldValue} to ${newValue}`) 
})


onBeforeMount(() => {
    fetch(`https://jsonplaceholder.typicode.com/posts/${postId.value}`)
        .then(response => response.json())
        .then(json => post.value = json)
})

const previousPost = () => {
    postId.value <= 0 ? postId.value-- : postId.value = 1
    postIds.value.push(postId.value)
}
const nextPost = () => {
    postId.value++
    postIds.value.push(postId.value)
}
</script>
 
<template>
    <div>
        <div class="flex flex-col space-y-3">
            <h1 class="text-2xl mb-5">Watch Example</h1>
            <p>
                <strong>Post ID:</strong> {{ postId }}
            </p>
            <p>
                <strong>Post Title:</strong> {{ post.title }}
            </p>
            <p>
                <strong>Post Body:</strong> {{ post.body }}
            </p>

        </div>
        <div class="mt-5">
            <button @click="previousPost()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                Previous Post
            </button>
            <button @click="nextPost()" class="ml-5 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                Next Post
            </button>
        </div>
    </div>
</template>
 
<style scoped></style>