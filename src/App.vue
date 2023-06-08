<template>
  <TodoList/>
</template>

<script>
import TodoList from './components/TodoList';

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-image: url('assets/background.png');
  position: absolute;
  width: 100%;
  height: 100vh;
  background-repeat: repeat;
  background-size: cover;
  background-position: center;
}
</style>
