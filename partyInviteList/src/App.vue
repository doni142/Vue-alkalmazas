<script setup>
import { ref } from 'vue';
import TodoDelete from './components/TodoDelete.vue';
import TodoUpdate from './components/TodoUpdate.vue';
const todo = ref('')
const nameList = ref([
  {title: 'Jenő'},
  {title: 'Pista'},
  {title: 'Judit'},
  {title: 'Erika'}
])
const state = ref('new')
let editedTodo = null

function add () {
  nameList.value.push({ title: todo.value }) // lista értékhez pusholja az új szó értékét
  todo.value = '' // üressé tesszük, hogy új szót addhassunk hozzá 
}

function remove () {
  nameList.value = nameList.filter(actual => actual.title != todo.title)
} // lista érték = lista filter törlés függvény. actual => actual szöveg nem egyenlő todo szöveggel

function update (id) {
  todo.value = nameList.value[id].title //todo.értékét =vé teszük a listánk érték[id].title-jével
  state.value = 'save' // state értékét =vé teszük a save-val
  editedTodo = id // szerkesztetTodonk =vé teszük a az id-vel
}

function save () {
  nameList.value[editedTodo].title = todo.value // lista érték szerk.todo.title egyenlővé teszük a todo értékével
  todo.value = '' // todo értékét üressé tesszük
  state.value = 'add' // státusz állapot értékét be állítjuk add -ra
}

</script>
<template>
<ul>
  <li v-for="(todo, key) in nameList" :key="key">
    {{ todo.title }}
    <TodoDelete :todo="todo" @todo-del="remove"/>
    <TodoUpdate :id="key" @todo-edit="update"/>
  </li>
</ul>
<input type="text" v-model="todo">
<button @click="save" v-if="state =='save'">save</button>
<button @click="add" v-if="state =='add'">add</button>
</template>
<style scoped>

</style>