<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Create</button>
    <SelectFilter @func="func"/>
  </form>
</template>

<script>
import SelectFilter from '@/components/SelectFilter'
export default {
  data () {
    return {
      title: ''
    }
  },
  components: {
    SelectFilter
  },
  computed: {

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
    },
    func (value) {
      this.$emit('func', value)
    }
  }
}
</script>

<style scoped lang="sass">
form
  display: flex
  align-items: center
  justify-content: space-between
  height: 2rem
  margin-bottom: 1rem

  $width: 8rem
  $mlButton: 1rem
  $height: 1.4rem
  $padding: .2rem

  input
    height: $height
    width: calc(100% - #{$width} - #{$mlButton})
    padding: $padding
    border: 1px solid #ccc

  button
    width: $width
    height: 1.9rem
    margin-left: $mlButton
    padding: $padding
    border: 1px solid #ccc
    color: #2c3e50
    transition: all .2s ease-out
    &:hover
      background-color: #e8e8e8
    &:active
      background-color: #cfcfcf

</style>
