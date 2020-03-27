<template>
    <section class="content">
        <h1 class="content__heading"><i class="fas fa-check"></i>ToDo List</h1>
        <div class="content__list-container">
            <div class="todo-list">
                <todoComponent />
            </div>
        </div>
    </section>
</template>

<script>
import todoComponent from '@/components/todoComponent.vue'

export default {
    components: {
        todoComponent
    }
}

</script>

<style scoped>

.content {
    margin: auto;
    margin-top: 10vh;
    width: 50%;
    height: auto;
    font-family: 'Open Sans', sans-serif;
    text-align: center;
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

</style>