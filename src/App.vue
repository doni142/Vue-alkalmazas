<script setup>
  import { ref } from 'vue';
  const count = ref(0)
  /* const attributs = {
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
  } */
  /* function toggle(){}
  const valtozo = ref("walami") */

 /*  function render(){
    const newH1 = document.createElement("h1");
    const newH1Content = document.createTextNode("Jó napot");
    newH1.appendChild(newH1Content);

    const newP = document.createElement("p");
    const newPContent = document.createTextNode("egy két há");
    newP.appendChild(newPContent);

    const a = document.createAttribute("class");
    a.value = valtozo;
    newP.setAttribute(a);
    newP.addEventListener('click', toggle);

    const newDiv = document.createElement("div");
    newDiv.appendChild(newH1);
    newDiv.appendChild(newP);

    const currentDiv = document.getElementById("div1");
    document.body.insertBefore(newDiv, currentDiv);
  }  */
</script>

<template>
  <!-- <p :class="count" class="count">ValamiValamiValamiValami</p> --> <!-- : => v-bind:-->
  <p v-bind="attributs"></p>
  <div class="box" :class="status">
    <h1 v-on:click="toggle">Vue</h1>
    <p>Lorem ipsum</p>
  </div>
  <div>
    
    <input type="text" v-model="count">
    <p> {{count}} </p>
    <button @click="count++">  
      increment
    </button> 
  </div>
  <div>
    <h1>Jó napot</h1>
    <p>egy két há</p>
  </div>
</template>
<!-- @ ==> v-on: -->
<!-- <input type="text" :value="count" v-on:input="event => count = event.target.value"> -->
<style scoped>
  .box p{
    color: red;
    display: block;
  }
  .box.closed p{
    display: none;
  }
</style>
<!-- HF: 1 Legyen egy olyan div amiben van h1 és p 2. másik div amiben egy sima szöveg doboz van meg egy textarea -->
