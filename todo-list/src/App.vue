<template>
  <div id="app">
    <todoList :data="db" 
    @addData="addData" 
    @deleteData="deleteData" 
    @changeData="changeData" />
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
      this.lastId++
    },

    deleteData: function(id) {
      this.db.splice(id - 1, 1)
    },

    changeData(changeElementArray) {
      this.db[changeElementArray[0] - 1].text = changeElementArray[1]
      console.log(changeElementArray[0])
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
