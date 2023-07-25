<script setup>
import { ref } from 'vue';
import bLDelet from './components/bLDelet.vue';
import bLUpdate from './components/bLUpdate.vue';

const vasarolni = ref('')
const lista = ref ([
  {title : 'kifli'},
  {title : 'kenyér'},
  {title : 'tejföl'},
  {title : 'felvágott'}
])
const state = ref('new')
let editedvasarlas = null

function add () {
  lista.value.push({title: vasarolni.value})
  vasarolni.value = ''
} 

function del (vasarolni) {
  console.log(vasarolni)
  lista.value = lista.value.filter(actual => actual.title != vasarolni.title)
}

function update (actualvenni) {
  vasarolni.value = lista.value[actualvenni].title
  state.value = 'save'
  editedvasarlas = actualvenni
}
 
function save () {
  console.log(editedvasarlas, lista.value[editedvasarlas])
  lista.value[editedvasarlas].title = vasarolni.value
  vasarolni.value = ''
  state.value = 'new'
}
</script>

<template>
<ul>
  <li v-for="(vasarolni, key) in lista">
  {{ vasarolni.title }}
  <bLDelet :vasarolni="vasarolni" @vasarolni-del="del"/>
  <bLUpdate :id="key" @vasarolni-edit="update"/>
  </li>
</ul>

<input type="text" v-model="vasarolni">
<button @click="add" v-if="state == 'new'">Add</button>
<button @click="save" v-if="state == 'save'">Save</button>

</template>

<style scoped>

</style>
