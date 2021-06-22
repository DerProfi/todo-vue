<template>
  <div>
      <input type="text" class="todo-input" placeholder="What needs to be done?" v-model="newTodo" @keyup.enter="addTodo" autofocus>
      <div v-for="(todo, index) in todos" :key="todo.id" class="todo-item">
          <div class="todo-container-left">
              <input type="checkbox" v-model="todo.completed">
              <div v-if="!todo.editing" class="todo-label" :class="{completed: todo.completed}" @dblclick="editTodo(todo)">{{todo.title}}</div>
              <input v-else type="text" v-model="todo.title" class="todo-edit" @blur="exitEdit(todo)" @keyup.enter="exitEdit(todo)">
          </div>
          <button class="remove-button" @click="removeTodo(index)">
              done
          </button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'todo-list',
  data () {
    return {
      newTodo: '',
      idForTodo: 3,
      todos: [
          {
            'id': 1,
            'title': 'Finish Vue Todo-App',
            'completed': false,
            'editing': false,
          },
          {
            'id': 2,
            'title': 'Talk to Leandro',
            'completed': false,
            'editing': false,
          },
      ]
    } 
  },
  methods: {
      addTodo(){
          if (this.newTodo === "") {
              return
          }
          this.todos.push(
              {
                  id: this.idForTodo,
                  title: this.newTodo,
                  completed: false,
              }
          )
          this.newTodo = ''
          this.idForTodo++
      },
      removeTodo(index) {
          this.todos.splice(index, 1);   
      },
      editTodo(todo){
          todo.editing = true;
      },
      exitEdit(todo){
          todo.editing = false;
      }
  }
}
</script>

<style>
.todo-input{
    width: 100%;
    padding: 10px 18px;
    font-size: 18px;
    margin-bottom: 16px;
}

.todo-item{
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.remove.button{
    cursor: pointer;
    margin-left: 14px;
}

button:hover {
    background-color: black;
    color: white;
}

.todo-container-left{
    display: flex;
    align-items: center;
} 

.todo-label{
    font-size: 18px;
    padding: 10px;
    border: 1px solid white;
    margin-left: 12px;
}

.todo-edit{
    font-size: 18px;
    margin-left: 12px;
    width: 100%;
    padding: 10px;
    border: 1px solid white;
}

.completed{
    text-decoration: line-through;
    color: grey;
}

</style>
