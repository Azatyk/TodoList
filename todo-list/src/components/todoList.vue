<template>
    <div class="container">
    <addForm @cancel="cancelForm" :cancelState="cancelState" v-show="cancelState" />
    <section class="content" :class="{'blur': cancelState}">
        <h1 class="content__heading"><i class="fas fa-check"></i>ToDo List</h1>
        <div class="content__list-container">
            <div class="todo-list">
                <todoComponent  v-for="element in data" :key="element.id" 
                :text="element.text" />
            </div>
        </div>
    </section>
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
            cancelState: true
        }
    },

    methods: {
        cancelForm: function() {
            console.log('Click')
            this.cancelState = false
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
    width: 100%;
    padding: 0.1px;
    height: 100vh;
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
    padding-top: 25px;
    padding-bottom: 5px;
    padding-left: 20px;
    padding-right: 20px;
    width: 100%;
    min-height: 50px;
    background-color: white;
    border-radius: 30px;
}

</style>