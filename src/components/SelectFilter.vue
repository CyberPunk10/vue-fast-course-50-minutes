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
  // watch: {
  //   filter (value) {
  //     console.log(value)
  //   }
  // },
  computed: {
    selectedFilter () {
      if (this.filter === 'all') {
        return 'all'
      }
      if (this.filter === 'completed') {
        return 'completed'
      }
      if (this.filter === 'not-completed') {
        return 'not-completed'
      }
      return null
    }
  },
  methods: {
    pushFilterOption (selectedFilter) {
      this.$emit('push-filter', selectedFilter)
    }
  }
}
</script>
