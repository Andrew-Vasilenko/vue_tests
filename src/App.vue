<template>
  <div id="app">
    <h1>Todo List</h1>
    <hr>
    <AddTodoItem
      v-on:todoItemAdd = "todoItemAdd"
    />
    <TodoList
      v-bind:todoList = "todoList"
      v-on:todoItemRemove = "todoItemRemove"
      v-on:todoItemSaveChanges = "todoItemSaveChanges"
    />
  </div>
</template>

<script>
  // импорт компонентов
  import TodoList from '@/components/TodoList'
  import AddTodoItem from '@/components/AddTodoItem.vue'

  export default {
    name: 'App',
    data() {
      return {
        todoList: [
          {id:1, title:"Born", completed:false},
          {id:2, title:"Live", completed:false},
          {id:3, title:"Die", completed: false}
        ]
      }
    },
    // регистрация компонентов
    components: {
      TodoList:TodoList,
      AddTodoItem:AddTodoItem
    },
    methods: {
      todoItemAdd(newTodoItem){
        this.todoList.push(newTodoItem)
      },
      todoItemRemove(todoItemId){        
        this.todoList = this.todoList.filter(todoItem => todoItem.id !== todoItemId)
      },
      todoItemSaveChanges(editedTodoItem){
        this.todoList[editedTodoItem.index].title = editedTodoItem.newTitle
      }
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
