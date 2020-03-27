<template>
    <div class="component">
        <p class="component__paragraph">{{ text }}</p>
        <button class="component__check-button"><i class="fas fa-check-circle"></i></button>
        <button class="component__change-button"><i class="fas fa-edit"></i></button>
        <button class="component__delete-button"><i class="fas fa-minus-circle"></i></button>
    </div>
</template>

<script>
export default {
    props: {
        text: {
            type: String,
            required: true
        }
    }
}
</script>

<style scoped>

.component {
    
}

</style>