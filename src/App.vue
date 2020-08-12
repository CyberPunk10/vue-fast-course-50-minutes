<template>
  <div id="app">
    <h1>Todo Application</h1>
    <hr>
    <router-link to="/">Home</router-link>
    <router-link to="/todos">Todos</router-link>
    <a href="https://www.youtube.com/watch?v=OlnwgS-gk8Y">Ссылка на урок</a>
    <hr>

    <div class="cntr">
      <router-view/>
    </div>
  </div>
</template>

<style lang="sass">
#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50

  a
    display: inline-block
    margin: .5rem 1rem

  .cntr
    max-width: 40rem
    margin: 0 auto

</style>
