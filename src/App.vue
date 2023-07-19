<script setup>
  import ButtonCounter from './components/ButtonCounter.vue'

  function megnyomtak (count){
    console.log("megnyomtak", count)
  }
  
</script>

<template>
 <ButtonCounter title="Megnyomtad" count="5" @megnyomtak="megnyomtak" />
 <ButtonCounter title="Klikk" />
</template>
<style scoped>
  
</style>
