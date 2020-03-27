<template>
  <div id="app">
    <todoList />
  </div>
</template>

<script>
import todoList from '@/components/todoList.vue'

export default {
  components: {
    todoList
  }
}

</script>

<style>

* {
  margin: 0;
  padding: 0;
  border: 0;
}

#app {
  width: 100%;
  padding: 0.1px;
  height: 100vh;
  font-family: 'Open Sans', sans-serif;
  background-color: #fdcb6e;
}

</style>
