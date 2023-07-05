<script setup>
  import { ref } from 'vue';
  const count = ref(0)
  const attributs = {
    id: "valami",
    class: "öt"
  } 
  let status = ref("closed")
  function toggle(){
    if (status.value == ""){
      status.value = "closed"
    }
    else {
      status.value = ""  
    }
    console.log("toggle")
  }

</script>

<template>
  <!-- <p :class="count" class="count">ValamiValamiValamiValami</p> --> <!-- : => v-bind:-->
  <p v-bind="attributs"></p>
  <div class="box" :class="status">
    <h1 v-on:click="toggle">Vue</h1>
    <p>Lorem ipsum</p>
  </div>
  <div>
    <!-- <input type="text" :value="count" v-on:input="event => count = event.target.value"> -->
    <input type="text" v-model="count">
    <p> {{count}} </p>
    <button @click="count++">  <!-- @ ==> v-on: -->
      increment
    </button> 
  </div>
</template>

<style scoped>
  .box p{
    color: red;
    display: block;
  }
  .box.closed p{
    display: none;
  }
</style>
