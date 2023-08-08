<script setup>
import { ref } from 'vue';
import bLDelet from './components/bLDelet.vue';
import bLUpdate from './components/bLUpdate.vue';

const vasarolni = ref('')
const lista = ref ([])
const state = ref('new')
let editedvasarlas = null

async function refreshLista() {
  const response = await fetch('http://127.0.0.1:8000/api/todos')
  const freshLista = await response.json()
  lista.value = freshLista
}
refreshLista()

async function add () {
  // lista.value.push({title: vasarolni.value})
  await fetch('http://127.0.0.1:8000/api/todos', {
    method: 'POST', 
    body: JSON.stringify({ 'title': vasarolni.value }),
    headers : {
      "Content-Type": "application/json"
    }
  })
  vasarolni.value = ''
  await refreshLista()
} 

async function del (vasarolni) {
  console.log(vasarolni)
  // lista.value = lista.value.filter(actual => actual.title != vasarolni.title)
  const url = 'http://127.0.0.1:8000/api/todos/' + vasarolni.id
  await fetch (url, {method: 'DELETE'}) 
  await refreshLista()
}

function update (actualvenni) {
  vasarolni.value = actualvenni.title
  state.value = 'save'
  editedvasarlas = actualvenni
}
 
async function save () {
  // console.log(editedvasarlas, lista.value[editedvasarlas])
  //lista.value[editedvasarlas].title = vasarolni.value
  const url = 'http://127.0.0.1:8000/api/todos/' + editedvasarlas.id

  await fetch (url, {
    method: 'PATCH', 
    body: JSON.stringify({ 'title': vasarolni.value }),
    headers : {
      "Content-Type": "application/json"
    }
  })

  vasarolni.value = ''
  state.value = 'new'
  await refreshLista()
}

</script>

<template>
<ul>
  <li v-for="(vasarolni) in lista">
  {{ vasarolni.title }}
  <bLDelet :vasarolni="vasarolni" @vasarolni-del="del"/>
  <bLUpdate :vasarolni="vasarolni" @vasarolni-edit="update"/>
  </li>
</ul>

<input type="text" v-model="vasarolni">
<button @click="add" v-if="state == 'new'">Add</button>
<button @click="save" v-if="state == 'save'">Save</button>

</template>

<style scoped>

</style>
