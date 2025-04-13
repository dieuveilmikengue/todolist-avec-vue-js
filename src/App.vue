<template>
  <main class="container">
    <h1>LISTE DES TACHES</h1>
  </main>
  <div class="container">
    <form action="" @submit.prevent="addTodo">
      <fieldset role="group">
        <input placeholder="Tache à faire" v-model="newTodo" />
        <button :disabled="newTodo.length === 0">Ajouter</button>
      </fieldset>
    </form>
    <div class="liste" v-if="todos.length === 0">Vous n'avez pas de taches à faire</div>
    <div class="liste" v-else>
      <ul>
        <li v-for="todo in todos" :key="todo.date" :class="{completed: todo.completed}">
          <label for="">
            <input class="completed" type="checkbox" v-model="todo.completed">
            {{ todo.title }} ( {{ todo.date }} )
          </label>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const newTodo = ref("")
const todos = ref([])
const addTodo = () => {
  todos.value.push({
    title: newTodo.value,
    completed: false,
    date: new Date()
  })
  newTodo.value = ""
}
</script>

<style>
.completed{
  opacity: 0.5;
  text-decoration: line-through;
}

</style>