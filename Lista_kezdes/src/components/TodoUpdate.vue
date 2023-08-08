<script setup>
import { defineProps } from 'vue';

const props = defineProps(['id'])
const emit = defineEmits(['todo-edit'])

function update () {
    emit('todo-edit', props.id)
}
</script>
<template>
    <button @click="update">
        update
    </button>
</template>