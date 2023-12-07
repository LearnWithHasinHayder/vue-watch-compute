<script setup>
import { ref, watch, computed } from 'vue'

const items = ref([16,2,4])
const total = ref(0)

watch(items, (newItems, oldItems) => {
    console.log(newItems, oldItems)
    total.value = newItems.reduce((acc, item) => acc + item, 0)
}, { deep: true, immediate: true  })

function addRandomItem() {
    items.value.push(Math.floor(Math.random() * 100))
}

</script>
 
<template>
    <div>
        <div class="flex flex-col space-y-3">
            <h1 class="text-2xl mb-5">Watch Example</h1>
            <p>
               Values : {{ items }}
            </p>
            <p>
                Total = {{ total }}
            </p>


        </div>
        <div class="mt-5">
            <button @click="addRandomItem()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
               Add Item
            </button>
        </div>
    </div>
</template>
 
<style scoped></style>