<script setup>
import { ref, computed } from 'vue'
const n1 = ref(4)
const n2 = ref(12)


const getTotal = () => {
    console.log('Function called')
    return n1.value + n2.value
}

const computedTotal = computed(() => {
    console.log('Computed called')
    return n1.value + n2.value
})

</script>
 
<template>
    <div class="">
        <h1 class="text-2xl mb-5">Computed Cache</h1>
        <p>N1 = {{ n1 }}</p>
        <p>N2 = {{ n2 }}</p>
        <div class="flex flex-between mt-5">

            <div class="flex space-y-4 flex-col w-1/2">
                <p>Result {{ getTotal() }}</p>
                <p>Result {{ getTotal() }}</p>
                <p>Result {{ getTotal() }}</p>
                <p>Result {{ getTotal() }}</p>
                <p>Result {{ getTotal() }}</p>
            </div>
            <div class="flex space-y-4 flex-col">
                <div class="flex space-y-4 flex-col">
                    <p>Result {{ computedTotal }}</p>
                    <p>Result {{ computedTotal }}</p>
                    <p>Result {{ computedTotal }}</p>
                    <p>Result {{ computedTotal }}</p>
                    <p>Result {{ computedTotal }}</p>
                </div>
            </div>

        </div>
        <button @click="n1=2;n2=6" class="mt-5 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
            Change Number
        </button>
    </div>
</template>
 
<style scoped></style>