<template>
  <div>
    <li>
      <label v-bind:class="{done: todo.completed}">
        <input
          type="checkbox"
          v-on:change="todo.completed=!todo.completed">
        <strong>{{ index + 1 }}</strong>
        {{ todo.title | uppercase}}
      </label>
      <button
        class="rm"
        v-on:click="$emit('remove-todo', todo.id)"
      >&times;</button>
    </li>
  </div>
</template>

<script>
export default {
  name: 'todolist',
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase (value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped lang="sass">
li
  display: flex
  justify-content: space-between
  align-items: center
  height: 3rem
  margin-bottom: 0.5rem
  border: 1px solid #cfcfcf
  label
    input
      display: inline-block
      margin: 0 2rem
      height: 1.2rem
      width: 1.2rem
    strong
      margin-right: 2rem
    &.done
      text-decoration: line-through
  .rm
    height: 2rem
    width: 2rem
    font-size: 2rem
    color: #bbb
    display: flex
    justify-content: center
    align-items: center
    border: 1px solid #cfcfcf
    margin-right: .5rem
    outline: none
    background-color: #fff
    transition: background-color .2s ease-out

    &:hover
      background-color: #efefef
    &:active
      color: #aaa
      border-color: #bbb

</style>
