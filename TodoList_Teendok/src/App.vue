<script setup>
import { ref } from 'vue';
import TodoRemove from './components/TodoRemove.vue';
import TodoUpdate from './components/TodoUpdate.vue';

const todo = ref('')
const teendok = ref([
  {title: 'konyha'},
  {title: 'fürdő'},
  {title: 'hálószoba'},
  {title: 'előtér'}
])
const state = ref('new')
let editedTodo = null

function add(){
  teendok.value.push({ title: todo.value })
  todo.value = ''
}

function remove(todo){
  console.log(todo)
  teendok.value = teendok.value.filter(actual => actual.title != todo.title)
}

function edit(actualtodo){
  todo.value = teendok.value[actualtodo].title
  state.value = 'save'
  editedTodo = actualtodo
}

function save(){
  console.log(editedTodo, teendok.value[editedTodo])
  teendok.value[editedTodo].title = todo.value
  todo.value = ''
  state.value = 'add'
}

</script>
<template>
  <ul>
    <li v-for="(todo, key) in teendok" :key="key">
      {{ todo.title }}
      <TodoRemove :todo="todo" @todo-remove="remove"/>
      <TodoUpdate :id="key" @todo-edit="edit"/>
    </li>
  </ul>

  <input type="text" v-model="todo">
  <button @click="save" v-if="state =='save'">SAVE</button>
  <button @click="add" v-if="state == 'add'">ADD</button>

</template>