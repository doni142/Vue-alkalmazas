<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['todo'])
const emits = defineEmits(['todo-del'])

function Del(){
    emits('todo-del', props.todo)
}
</script>

<template>
    <button @click="Del">Delete</button>
</template>