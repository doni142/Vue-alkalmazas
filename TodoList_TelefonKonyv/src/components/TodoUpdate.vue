<script setup>
import { defineEmits, defineProps } from 'vue';

const props = defineProps(['id'])
const emits = defineEmits(['todo-update'])
function Update() {
    emits('todo-update', props.id)
}
</script>
<template>
    <button @click="Update">Update</button>
</template>