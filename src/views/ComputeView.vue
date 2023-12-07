<script setup>
import { ref, computed } from 'vue'
const n1 = ref(0)
const n2 = ref(0)


function getTotal() {
    return n1.value + n2.value
}


// const computedTotal = computed(()=>n1.value + n2.value)

const computedTotal = computed(() => {
    return n1.value + n2.value
})
</script>
 
<template>
    <div class="flex flex-col space-y-2">
        <h1>Compute</h1>
        <input type="number" v-model="n1" />
        <input type="number" v-model="n2" />

        <p>Result: {{ getTotal() }}</p>
        <p>Result: {{ computedTotal }}</p>
    </div>
</template>
 
<style scoped></style>