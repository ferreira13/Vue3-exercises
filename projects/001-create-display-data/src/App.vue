<template>
  <div>
    <h1 v-once v-text="title"></h1>
    <h2 v-text="subtitle"></h2>
    <div>
      <div v-if="todos.length">
        <h3>There {{ todos.length > 1 ? `are ${todos.length} todos` : `is a todo` }}</h3>
        <ul>
          <li v-for="(todo, index) in todos" :key="index">{{ todo }}</li>
        </ul>
      </div>
      <h3 v-else>There aren't any todos to display</h3>
    </div>
  </div>
</template>

<script>
import { faker } from '@faker-js/faker'

export default {
  name: 'lv-tarefas',
  data() {
    return { title: 'todo list', subtitle: 'Set the description', todos: [] }
  },
  mounted() {
    setInterval(() => this.todos.push(faker.lorem.sentences({ min: 1, max: 1 })), 2000)
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /* text-align: center; */
  margin-top: 10px;
}
</style>
