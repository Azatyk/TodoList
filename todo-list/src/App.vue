<template>
  <div id="app">
    <todoList :data="db" />
  </div>
</template>

<script>
import todoList from '@/components/todoList.vue'

export default {
  components: {
    todoList
  },

  data() {
    return {
      db: [
        {
          id: 1,
          text: "Покушать котлетки"
        },
        {
          id: 2,
          text: "Покушать шарлотку"
        }
      ]
    }
  }
}

</script>

<style>

* {
  margin: 0;
  padding: 0;
  border: 0;
}

</style>
