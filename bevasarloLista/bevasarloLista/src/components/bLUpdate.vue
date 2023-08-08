<script setup>
import { defineProps } from 'vue';

const editProps = defineProps(['vasarolni'])
const emit = defineEmits(['vasarolni-edit'])

function edit () {
    emit('vasarolni-edit', editProps.vasarolni)
}

</script>
<template>
    <button @click="edit">edit</button>
</template>