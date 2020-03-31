<template>
    <label for="changeInput"><div class="component" :class="{'strikethrough-background': isStrikethrough, 'change': isChange}">
        <div class="component__text-container">
            <span class="component__dash">—</span>
            <p class="component__paragraph" :class="{'strikethrough-text': isStrikethrough}" v-if="isChange == false">{{ this.element.text }}</p>
            <input v-focus id="changeInput" type="text" placeholder="Write something" v-model="inputValue" class="component__input" v-else>
        </div>
        <div class="component__buttons-container">
            <button class="component__check-button button" v-if="isStrikethrough == false" @click="isStrikethrough = true" :disabled="isChange" :class="{'disabled': isChange}"><i class="fas fa-check-circle"></i></button>
            <button class="component__uncheck-button button" v-else @click="isStrikethrough = false"><i class="fas fa-times-circle"></i></button>
            <button class="component__change-button button" v-if="isChange == false" :disabled="isStrikethrough" :class="{'disabled': isStrikethrough}" @click="isChange = true"><i class="fas fa-edit"></i></button>
            <button class="component__finish-button button" v-else @click="changeComponent"><i class="fas fa-flag-checkered"></i></button>
            <button class="component__delete-button button" @click="deleteComponent"><i class="fas fa-trash-alt"></i></button>
        </div>
    </div></label>
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
            isStrikethrough: false,
            isChange: false,
            inputValue: this.element.text
        }
    },

    methods: {
        deleteComponent: function() {
            this.$emit('deleteComponent', this.element.id)
        },

        changeComponent: function() {
            this.isChange = false
            this.$emit('changeComponent', [this.element.id, this.inputValue])
            // console.log(this.element.id, this.inputValue)
            // console.log('Type of id:', typeof this.element.id)
            // console.log('Type of input value:', typeof this.inputValue)
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
    cursor: text;
}

.change {
    background-color: #f39c12;
}

.component__text-container {
    width: 90%;
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

.component__input {
    width: 95%;
    font-size: 16px;
    font-family: 'Open Sans', sans-serif;
    color: #dff9fb;
    background: none;
    outline: none;
}

input::-webkit-input-placeholder { 
    color: #bdc3c7; 
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

.component__finish-button:hover {
    color: #2ecc71;
}

.component__delete-button:hover {
    color: #ff7979;
}

</style>