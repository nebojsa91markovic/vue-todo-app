<template>
  <div id="app">
    <h1>Vue Todo App </h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/TodoList'

export default {
  name: 'App',
  components: {
    TodoList,
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1f2c38;
  margin-top: 60px;
  font-size: 24px;
}

body {
    background-color: yellowgreen;
}
</style>
