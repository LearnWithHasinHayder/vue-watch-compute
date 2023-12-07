<script setup>
import { ref, watch, watchEffect } from 'vue'

const postId = ref(1)
const post = ref({});

const fName = ref('John')
const lName = ref('Doe')
const fullName = ref('');

function updateName(){
    fName.value = 'Keanu'
    lName.value = 'Reeves'
}


const fetchPost = () => {
    fetch(`https://jsonplaceholder.typicode.com/posts/${postId.value}`)
        .then(response => response.json())
        .then(json => post.value = json)
}

watchEffect(() => {
    fetchPost()
})

watchEffect(() => {
    fullName.value = `${fName.value} ${lName.value}`
})


const previousPost = () => {
    postId.value <= 1 ? postId.value = 1 : postId.value--
}
const nextPost = () => {
    postId.value++
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
            
            <p>
                <strong>First Name:</strong> {{ fName }}
            </p>
            <p>
                <strong>Last Name:</strong> {{ lName }}
            </p>
            <p>
                <strong>Full Name:</strong> {{ fullName }}
            </p>
        </div>
        <div class="mt-5">
            <button @click="previousPost()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                Previous Post
            </button>
            <button @click="nextPost()" class="ml-5 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                Next Post
            </button>
            <button @click="updateName()" class="ml-5 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
                Update Name
            </button>
        </div>
    </div>
</template>
 
<style scoped></style>