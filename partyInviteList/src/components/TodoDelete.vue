<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps(['todo'])
const emits = defineEmits(['todo-del'])
function Delete() {
    emits('todo-del', props.todo)
}
</script>
<template>
    <button @click="Delete">
        Delete
    </button>
</template>