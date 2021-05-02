<template>
    <div>
        <label for="todo-input">오늘할일</label>
        <input type="text" id="todo-input" @input="handleInput" :value="item">
        <button @click="addTodo" type="button" >추가</button>
    </div>
</template>

<script lang="ts">
    import Vue from 'vue'

    export default Vue.extend({
        props: {
            item: {
                type: String,
                required: true // 반드시 값을 내려 받는다.
            }
        },
        methods: {
            handleInput(event: InputEvent){
                const eventTarget = event.target as HTMLInputElement;
                this.$emit("input", eventTarget.value);
            },
            addTodo(){
               this.$emit('add')
            },
        }
    })
</script>

<style scoped>

</style>