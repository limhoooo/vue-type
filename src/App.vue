<template>
  <div>
    <header>
    <h1>Vue Todo with Typescript</h1>
    </header>
    <main>
    <todo-input :item="todoText" @input="updateTodoText" @add="addTodoItem"></todo-input>
    </main>
    <div>
      <ul>
        <TodoListItem>111</TodoListItem>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
import TodoInput from './components/TodoInput.vue'
import TodoListItem from './components/TodoListItem.vue';

const STORAGE_KEY = "vue-todo-ts-v1"
const storage = {
  save(todoItems: any){
    const parsed = JSON.stringify(todoItems)
    localStorage.setItem(STORAGE_KEY,parsed)
  },
  fetch(){
    const todoItems = localStorage.getItem(STORAGE_KEY) || '[]';
    const result = JSON.parse(todoItems);
    return result;
  }
}

  export default Vue.extend({
  components: { TodoInput, TodoListItem },
        data() {
            return {
                todoText: "",
                todoItems: [] as any[],
            }
        },
        methods: {
          updateTodoText(value: string){
            this.todoText = value;
          },
          addTodoItem(){
            const val = this.todoText;
            this.todoItems.push(val)
            storage.save(this.todoItems)
            //localStorage.setItem(val, val);
            this.initTodoText();
          },
          initTodoText(){
            this.todoText = '';
          },
          fetchTodoItems(){
            this.todoItems = storage.fetch();
          },
        },
        created(){
          this.fetchTodoItems();
        }
        
  })
</script>

<style scoped>

</style>