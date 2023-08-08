<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['todo'])
const emit = defineEmits(['todo-remove'])

function remove() {
    emit('todo-remove', props.todo)
}
</script>
<template>
    <button @click="remove">
        remove
    </button>
</template>