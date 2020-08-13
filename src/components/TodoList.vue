<template>
  <div>
    <ul>
      <TodoItem
        v-for="(t, i) in todos" :key="t.id"
        v-bind:todo="t"
        v-bind:index="i"
        v-on:remove-todo="removeTodo"
        />
    </ul>
  </div>
</template>

<script>
import TodoItem from '../components/TodoItem'

export default {
  name: 'todolist',
  props: [
    'todos'
  ],
  components: {
    TodoItem
  },
  methods: {
    removeTodo (id) {
      this.$emit('removeTodo', id)
    }
  }
}
</script>

<style scoped lang="sass">
ul
  max-width: 40rem
  list-style: none
  margin: 0
  padding: 0

</style>
