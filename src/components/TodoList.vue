<template>
  <div>
      <input type="text" class="todo-input" placeholder="What needs to be done?" v-model="newTodo" @keyup.enter="addTodo">
      <div v-for="(todo, index) in todos" :key="todo.id" class="todo-item">
          <div>
            {{todo.title}}
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
          },
          {
            'id': 2,
            'title': 'Talk to Leandro',
            'completed': false,
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

</style>
