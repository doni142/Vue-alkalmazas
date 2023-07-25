<script setup>
import { defineProps } from 'vue';

const delProps = defineProps(['vasarolni'])
const delEmit = defineEmits(['vasarolni-del'])

function del () {
  delEmit('vasarolni-del', delProps.vasarolni)
}

</script>
<template>
    <button @click="del">del</button>
</template>