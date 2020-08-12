<template>
  <select v-model="filter">
    <option value="all">All</option>
    <option value="completed">Completed</option>
    <option value="not-completed">Not completed</option>
  </select>
</template>

<script>
export default {
  data () {
    return {
      filter: 'all'
    }
  },
  watch: {
    filter (value) {
      this.$emit('func', value)
    }
  },
  computed: {

  },
  methods: {

  }
}
</script>

<style scoped lang="sass">
select
  width: 8rem
  height: 1.9rem
  margin-left: 1rem
  border: 1px solid #ccc
  color: #2c3e50
  transition: all .2s ease-out
  padding: 0 .2rem
  &:hover, &:focus
    border-color: #999

</style>
