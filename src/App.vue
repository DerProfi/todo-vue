<template>
  <div id="app" class="container">
    <img src="./assets/todo.png" alt="todo-symbol" class="symbol">
    <todo-list></todo-list>
    <br>
    <credits></credits>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import credits from './components/credits.vue'


export default {
  name: 'App',
  components: {
    TodoList,
    credits,
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

.container{
  max-width: 600px;
  margin: 0 auto;
}

.symbol{
  display: block;
  height: 75px;
  margin: 0 auto;
  margin-bottom: 10px;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
