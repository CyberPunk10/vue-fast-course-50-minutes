<template>
  <div>
    <li>
      <span>из item: {{ todo }} </span>
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
    }
  }
}
</script>
