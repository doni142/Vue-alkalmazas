<script setup>
import TodoUpdateVue from './components/TodoUpdate.vue';
import TodoDeleteVue from './components/TodoDelete.vue';
import { ref } from 'vue';

const todo = ref('')
const telefonkonyv = ref([
  {title: 'terminátor'},
  {title: 'ET'},
  {title: 'wall-e'}
])
const state = ref('new')
let editedTodo = null

function add() {
  telefonkonyv.value.push({title: todo.value})
  todo.value = ''
}

function del(todo) {
  console.log(todo)
  telefonkonyv.value = telefonkonyv.filter(actual => actual.title != todo.title)
}

function update(actualtodo) {
  todo.value = telefonkonyv.value[actualtodo].title
  state.value = 'save'
  editedTodo = actualtodo
}

function save() {
  console.log(editedTodo, telefonkonyv.value[editedTodo])
  telefonkonyv.value[editedTodo].title = todo.value
  todo.value = ''
  state.value = 'add'
}
</script>
<template>
  <ul>
    <li v-for="(todo, key) in telefonkonyv" :key="key">
      {{ todo.title }}
      <TodoDeleteVue :todo="todo" @todo-del="del"/>
      <TodoUpdateVue :id="key" @todo-update="update"/>
    </li>
  </ul>
  <input type="text" v-model="todo">
  <button @click="save" v-if="state=='save'">save</button>
  <button @click="add" v-if="state=='add'">add</button>
</template>