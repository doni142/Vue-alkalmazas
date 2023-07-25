<script setup>
import { defineProps } from 'vue';

const editProps = defineProps(['id'])
const emit = defineEmits(['vasarolni-edit'])

function edit () {
    emit('vasarolni-edit', editProps.id)
}

</script>
<template>
    <button @click="edit">edit</button>
</template>