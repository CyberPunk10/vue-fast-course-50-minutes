<template>
  <div id="app">
    <TodoList
      v-bind:todos="todos"
    />
    <!-- <router-view/> -->
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
export default {
  name: 'app',
  data () {
    return {
      todos: [
        { id: 1, title: 'Купить хлеб', complited: false },
        { id: 2, title: 'Купить масло', complited: false },
        { id: 3, title: 'Купить молоко', complited: false }
      ]
    }
  },
  components: {
    TodoList
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

</style>
