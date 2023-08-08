<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['id'])
const emits = defineEmits(['todo-edit'])
function Update() {
    emits('todo-edit', props.id)
}
</script>
<template>
    <button @click="Update">
        Update
    </button>
</template>