<template>
  <div id="app">
    <todoList :data="db" 
    @addData="addData" 
    @deleteData="deleteData" />
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
      lastId: 0,

      db: []
    }
  },

  methods: {
    addData: function(inputValue) {
      this.db.push({
        id: this.lastId + 1,
        text: inputValue
      })
    },

    deleteData: function(id) {
      this.db.splice(id - 1, 1)
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
