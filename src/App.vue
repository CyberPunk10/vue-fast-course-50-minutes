<template>
  <div id="app">
    <AddTodoElement
      @add-todo="addTodo"
    />
    <TodoList
      v-bind:todos="todos"
      v-on:removeTodo="removeTodo"
    />
    <!-- <router-view/> -->
  </div>
</template>

<script>
import AddTodoElement from '@/components/AddTodoElement'
import TodoList from '@/components/TodoList'
export default {
  name: 'app',
  data () {
    return {
      todos: [
        { id: 1, title: 'Купить хлеб', completed: false },
        { id: 2, title: 'Купить масло', completed: false },
        { id: 3, title: 'Купить молоко', completed: false }
      ]
    }
  },
  components: {
    TodoList, AddTodoElement
  },
  mounted () {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  methods: {
    removeTodo (id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },

    addTodo (newTodo) {
      this.todos.push(newTodo)
    }
  }
}
</script>

<style lang="sass">
#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  max-width: 40rem

</style>
