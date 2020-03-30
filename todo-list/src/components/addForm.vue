<template>
    <div class="add">
        <div class="black-layer"></div>
        <div class="add-content">
            <div class="add-content__heading">Add new task <span class="add-content__plus-icon"><i class="fas fa-plus-square"></i></span></div>
            <div class="add-content__adding">
                <input v-focus id="addInput" type="text" class="add-content__input" placeholder="Write anything" v-model="inputValue" :class="{'empty': isEmpty}">
                <div class="add-content__buttos-conntainer">
                    <button class="add-content__add-button button" @click="addComponent"><i class="fas fa-check"></i></button>
                    <button class="add-content__exit-button button" @click="cancel"><i class="fas fa-times"></i></button>
                </div>
            </div>
            <label for="addInput"><p v-if="isEmpty" class="add-content__danger-text">You should write some task here <i class="fas fa-arrow-up"></i></p></label>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            inputValue: '',
            isEmpty: false
        }
    },

    methods: {
        cancel: function() {
            this.$emit('cancel')
        },

        addComponent: function() {
            if(this.inputValue.trim() != '') {
                this.$emit('addComponent', this.inputValue)
                this.inputValue = ''
            } else {
                this.isEmpty = true
            }
        }
    },

        directives: {
        focus: {
            inserted: function(el) {
            el.focus()
            }
        }
    }
}
</script>

<style scoped>

.add {
    position: absolute;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.black-layer {
    position: absolute;
    width: 100%;
    height: 100vh;
    background-color: black;
    opacity: 0.8;
    z-index: 1;
}

.add-content {
    position: relative;
    padding: 10px;
    width: 30%;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: white;
    border-radius: 30px;
    z-index: 2;
}

.add-content__heading {
    width: 61%;
    font-size: 50px;
    font-style: italic;
    text-align: center;
    border-bottom: 4px solid #ffbe76;
}

.add-content__plus-icon {
    color: #ffbe76;
}

.add-content__adding {
    margin-top: 30px;
    margin-bottom: 15px;
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}

.add-content__input {
    padding: 5px 20px;
    height: 30px;
    width: 80%;
    color: #dff9fb;
    background-color: #0984e3;
    border-radius: 30px;
    outline: none;
}

.empty {
    border: 3px solid red;
}

input::-webkit-input-placeholder { 
    color: #bdc3c7; 
}

.add-content__buttos-conntainer {
    width: 10%;
    display: flex;
    align-items: center;
    justify-content: space-around;
}

.button {
    font-size: 25px;
    background: none;
    /* color: #0984e3; */
    transition: 0.2s ease-in-out;
    cursor: pointer;
    outline: none;
}

.add-content__add-button:hover {
    color: #badc58;
}

.add-content__exit-button:hover {
    color: #ff7979;
}

.add-content__danger-text {
    font-size: 20px;
    font-weight: 800;
    color: red;
    cursor: pointer;
}

</style>