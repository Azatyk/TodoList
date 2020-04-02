<template>
    <div class="container">
    <addForm @cancel="cancelForm" :cancelState="isCancel" v-if="isCancel"
    @addComponent="addData" />
    <section class="content" :class="{'blur': isCancel}">
        <h1 class="content__heading"><i class="fas fa-check"></i>ToDo List</h1>
        <div class="content__list-container">
            <div class="todo-list">
                <p v-if="data.length == 0" class="todo-list__no-content">There are no any tasks :c. <span class="todo-list__no-content todo-list__add-text" @click="openForm">Add it now!</span></p>
                <todoComponent  v-for="element in data" :key="element.id" 
                :element="element" 
                @deleteComponent="deleteData"
                @changeComponent="changeData" 
                v-else />    
            </div>
        </div>
    </section>
    <button class="form-button button" :class="{'blur': isCancel}" @click="openForm">Add new task</button>
    </div>
</template>

<script>
import todoComponent from '@/components/todoComponent.vue'
import addForm from '@/components/addForm.vue'

export default {
    props: {
        data: {
            type: Array,
            requred: true
        }
    },

    data() {
        return {
            isCancel: false
        }
    },

    methods: {
        cancelForm: function() {
            this.isCancel = false
        },

        addData: function(inputValue) {
            this.$emit('addData', inputValue)
            this.isCancel = false
        },

        deleteData: function(id) {
            this.$emit('deleteData', id)
        },

        changeData: function(changeElementArray) {
            this.$emit('changeData', changeElementArray)
            // console.log('Now changing data in todoList:')
            // console.log(changeElementArray)
        },

        openForm: function() {
            this.isCancel = true
        }
    },

    components: {
        todoComponent,
        addForm
    }
}

</script>

<style scoped>

.container {
    min-width: 100%;
    padding: 0.1px;
    min-height: 100vh;
    height: 100%;
    font-family: 'Open Sans', sans-serif;
    background-color: #ffbe76;
}

.content {
    margin: auto;
    margin-top: 10vh;
    width: 50%;
    height: auto;
    font-family: 'Open Sans', sans-serif;
    text-align: center;
    transition: 0.3s ease-in-out;
}

.blur {
    filter: blur(10px);
}

.content__heading {
    margin: auto;
    width: 30%;
    font-size: 50px;
    font-style: italic;
    border-bottom: 6px solid #0984e3;
}

.fa-check {
    margin-right: 15px;
    color: #0984e3;
}

.todo-list {
    margin-top: 10vh;
    margin-bottom: 20px;
    padding-top: 25px;
    padding-bottom: 5px;
    padding-left: 20px;
    padding-right: 20px;
    width: 100%;
    min-height: 50px;
    background-color: white;
    border-radius: 30px;
}

.todo-list__no-content {
    font-size: 20px;
    font-weight: 600;
}

.todo-list__add-text {
    font-style: italic;
    color: #0984e3;
    cursor: pointer;
}

.form-button {
    position: fixed;
    top: 12vh;
    right: 10%;
}

.button {
    padding: 10px 20px;
    font-size: 20px;
    font-weight: 600;
    background: none;
    border: 3px solid #0984e3;
    border-radius: 30px;
    transition: 0.3s ease-in-out;
    outline: none;
    cursor: pointer;
}

.button:hover {
    background-color: #0984e3;
    border: 3px solid #0984e3;
}

</style>