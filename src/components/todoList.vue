<template>
  <div>
    <ul>
      <TodoItem
        v-for="t in todos" :key="t.id"
        v-bind:todo="t"
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
  // data:
  components: {
    TodoItem
  }
}
</script>
