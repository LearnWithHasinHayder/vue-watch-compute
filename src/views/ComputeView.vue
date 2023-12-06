<script setup>
import { ref, computed } from 'vue'
const fName = ref('John')
const lName = ref('Doe')
//computed fullName with getter and setter
const fullName = computed({
    get: () => `${fName.value} ${lName.value}`,
    set: (value) => {
        const [newFName, newLName] = value.split(' ')
        fName.value = newFName
        lName.value = newLName??''
    }
})

</script>
 
<template>
    <div class="flex flex-col space-y-2">
        <h1>Compute</h1>
        <input v-model="fName" />
        <input v-model="lName" />

        <p>Result: {{ fullName }}</p>

        <input v-model="fullName">
    </div>
</template>
 
<style scoped></style>