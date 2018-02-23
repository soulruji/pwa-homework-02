<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoForm v-on:addTodo="addTodo"></TodoForm>
    <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoForm from './components/TodoForm.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);

    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1)
    },
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    }
  },
  created() {
    console.log(localStorage.length);
    if ( localStorage.length > 0) {
      for (var i =0; i < localStorage.length; i++) {
        console.log(localStorage.length);
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  components: {
    'TodoHeader': TodoHeader,
    'TodoForm': TodoForm,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter,
  }  
}
</script>

<style>
  body {
    text-align: center;
    background-color: #f2f2f2;
  }
  input {
    border: 1px solid #ccc;
    width: 200px;
  }
</style>
