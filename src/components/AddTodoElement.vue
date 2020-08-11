<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
</template>

<script>
export default {
  name: 'add-todo-element',
  data () {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit () {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo', newTodo)

        this.title = ''
      }
    }
  }
}
</script>

<style scoped lang="sass">
 form
    display: flex
    align-items: center
    height: 2rem
    margin-bottom: 1rem

    $width: 7rem
    $height: 1.4rem
    $padding: .2rem

    input
      height: $height
      width: calc(40rem - #{$width} - 1rem)
      padding: $padding
    button
      width: $width
      height: 2rem
      margin-left: 1rem
      padding: $padding

</style>
