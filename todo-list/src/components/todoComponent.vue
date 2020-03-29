<template>
    <div class="component" :class="{'strikethrough-background': isStrikethrough}">
        <div class="component__text-container">
            <span class="component__dash">—</span>
            <p class="component__paragraph" :class="{'strikethrough-text': isStrikethrough}">{{ this.element.text }}</p>
        </div>
        <div class="component__buttons-container">
            <button class="component__check-button button" v-if="isStrikethrough == false" @click="isStrikethrough = true"><i class="fas fa-check-circle"></i></button>
            <button class="component__uncheck-button button" v-else @click="isStrikethrough = false"><i class="fas fa-times-circle"></i></button>
            <button class="component__change-button button" :disabled="isStrikethrough" :class="{'disabled': isStrikethrough}"><i class="fas fa-edit"></i></button>
            <button class="component__delete-button button" @click="deleteComponent"><i class="fas fa-trash-alt"></i></button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        element: {
            type: Object,
            required: true
        }
    },

    data() {
        return {
            isStrikethrough: false
        }
    },

    methods: {
        deleteComponent: function() {
            this.$emit('deleteComponent', this.element.id)
        }
    }
}
</script>

<style scoped>

.component {
    margin-bottom: 20px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 10px 30px;
    background-color: #0984e3;
    border-radius: 30px;
    transition: 0.2s ease-in-out;
}

.component__text-container {
    display: flex;
    flex-direction: row;
    align-items: center;
}

.component__dash {
    margin-right: 10px;
    font-size: 20px;
    color: #dff9fb;
}

.component__paragraph {
    color: #dff9fb;
}

.component__buttons-container {
    width: 10%;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.button {
    font-size: 20px;
    color: #c7ecee;
    background: none;
    outline: none;
    cursor: pointer;
    transition: 0.2s ease-in-out;
}

.component__check-button:hover {
    color: #badc58;
}

.strikethrough-text {
    text-decoration: line-through;
}

.strikethrough-background {
    background-color: #2ecc71;
}

.component__uncheck-button:hover {
    color: #8e44ad;
}

.component__change-button:hover {
    color: #FFC312;
}

.disabled {
    color: #95a5a6;
    cursor: initial;
}

.disabled:hover {
    color: #95a5a6;
}

.component__delete-button:hover {
    color: #ff7979;
}

</style>