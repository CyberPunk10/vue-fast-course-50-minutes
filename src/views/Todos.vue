<template>
  <div>
    <h2>Todo Application</h2>
    <AddTodoElement
      @add-todo="addTodo"
    />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not completed</option>
    </select>
    <Loader v-if="loading"/>
    <TodoList
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      v-on:removeTodo="removeTodo"
    />
    <p v-else>No todos.</p>
  </div>
</template>

<script>
import AddTodoElement from '@/components/AddTodoElement'
import TodoList from '@/components/TodoList'
import Loader from '@/components/Loader'
export default {
  name: 'app',
  data () {
    return {
      todos: [
        { id: 1, title: 'Купить хлеб', completed: false },
        { id: 2, title: 'Купить масло', completed: false },
        { id: 3, title: 'Купить молоко', completed: false }
      ],
      loading: true,
      filter: 'all'
    }
  },
  components: {
    TodoList, AddTodoElement, Loader
  },
  mounted () {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.todos = json
          this.loading = false
        }, 500)
      })
  },
  // watch: {
  //   filter (value) {
  //     console.log(value)
  //   }
  // },
  computed: {
    filteredTodos () {
      if (this.filter === 'all') {
        return this.todos
      }
      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }
      if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      }
      return null
    }
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
