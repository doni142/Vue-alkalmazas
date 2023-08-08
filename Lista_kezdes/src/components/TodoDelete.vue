<script setup>
import { defineProps } from 'vue';

const props = defineProps(['todo'])
const emit = defineEmits(['todo-del'])
function del(){
    emit('todo-del', props.todo)
}
</script>
<template>
    <button @click="del">
        del
    </button>
</template>