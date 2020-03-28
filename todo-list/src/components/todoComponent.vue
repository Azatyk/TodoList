<template>
    <div class="component">
        <div class="component__text-container">
            <span class="component__dash">—</span>
            <p class="component__paragraph">{{ text }}</p>
        </div>
        <div class="component__buttons-container">
            <button class="component__check-button button"><i class="fas fa-check-circle"></i></button>
            <button class="component__change-button button"><i class="fas fa-edit"></i></button>
            <button class="component__delete-button button"><i class="fas fa-trash-alt"></i></button>
        </div>
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
    margin-bottom: 20px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 10px 30px;
    background-color: #0984e3;
    border-radius: 30px;
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

.component__change-button:hover {
    color: #FFC312;
}

.component__delete-button:hover {
    color: #ff7979;
}

</style>