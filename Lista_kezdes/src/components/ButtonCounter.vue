<script setup>
    import { ref, defineProps} from 'vue';
    const count = ref(0)
    const props = defineProps(['title', 'count'])
    count.value = props.count ? props.count : 0
    console.log(props.count)
    const emit = defineEmits(['megnyomtak'])
    function klikk () 
    {
        count.value++
        emit('megnyomtak', count.value)
    }
</script>
<template>
<button @click="klikk"> {{ title }} : {{ count }}</button>
</template>