<template>
  <div id="app" class="container">
      <div class="page-header">
          <h1>Vue.Js Todo App</h1>
      </div>
    <todo-list v-bind:todos="todos"></todo-list>
    <form v-on:submit.prevent="addNewTodo()">
        <div class="form-group">
            <input v-model="newTodoText" type="text" class="form-control" name="name" placeholder="Enter new Todo here">
        </div>
    </form>
  </div>
</template>

<script>
import TodoList from './components/TodoList'

export default {
  components: {
    TodoList
  },
  data () {
    return {
      newTodoText: '',
      todos: [
        {
          title: 'Todo 1',
          done: false
        },
        {
          title: 'Todo 2',
          done: false
        },
        {
          title: 'Todo 3',
          done: false
        },
        {
          title: 'Todo 4',
          done: false
        }
      ]
    }
  },
  methods: {
    addNewTodo () {
      if (this.newTodoText.length > 0) {
        this.todos.push({
          title: this.newTodoText,
          done: false
        })
        this.newTodoText = ''
      }
    }
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
</style>
