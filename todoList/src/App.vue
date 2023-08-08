<script setup>
import { ref } from 'vue';
import TodoDelete from './components/TodoDelete.vue';
import TodoUpdate from './components/TodoUpdate.vue';

const todo = ref('')
const todos = ref([
    {title: 'alma'},
    {title: 'barack'},
    {title: 'körte'}
])
const state = ref('new')
let editedTodo = null

function add (){
  todos.value.push( {title: todo.value})
  todo.value = ''
}

function del (todo){
  console.log(todo)
  todos.value = todos.value.filter(actual => actual.title != todo.title)
}

function update (actualtodo) {
  todo.value = todos.value[actualtodo].title
  state.value = 'save'
  editedTodo = actualtodo
}

function save (){
  console.log(editedTodo, todos.value[editedTodo])
  todos.value[editedTodo].title = todo.value
  todo.value = ''
  state.value = 'new'
}
</script>

<template>
 <ul>
  <li v-for="(todo, key) in todos">
    {{ todo.title }}
    <TodoDelete :todo="todo" @todo-del="del"/>
    <TodoUpdate :id="key" @todo-edit="update"/>
  </li>
 </ul>

<input type="text" v-model="todo">
<button @click="save" v-if="state == 'save'">Save</button>
<button @click="add" v-if="state == 'new'">Add</button>

</template>
<style scoped>
  /* Edit = szerkesztés, CRUD = Create, Read, Update, Delete
  function valami(ertek) {return ertek>10}
  const valami = ertek => ertek > 10
  akarmi.map(ertek => ertek > 10)
  akarmi.map(function (ertek){return ertek>10})
  HF Ugyanezt megcsinálni todo helyett bevásárló lista, mit kell vennem.
*/
</style>