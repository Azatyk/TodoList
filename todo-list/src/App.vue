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
      for(let i = 0; i < this.db.length; i++) {
        if(this.db[i].id == id) {
          this.db.splice(i, 1)
        }
      }
    },

    changeData(changeElementArray) {
      for(let i = 0; i < this.db.length; i++) {
        if(this.db[i].id == changeElementArray[0])  {
          this.db[i].text = changeElementArray[1]
        }
      }
      console.log('changeData' + changeElementArray[0])
      console.log('Changing data:', changeElementArray)
      console.log('Type of recieving id:', typeof changeElementArray[0])
      console.log('Type of recieving text', typeof changeElementArray[1])
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
