
<template>
  <div id="app">
    <Header></Header>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <List v-bind:propsdata="todoItems" @remove="remove"></List>
    <Clear v-on:removeAll="clear"></Clear>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import TodoInput from './components/TodoInput.vue'
import List from './components/List.vue'
import Clear from './components/Clear.vue'

export default {

  name: 'App',

  data() {
    return {
      todoItems: []
    }
  },

  created() {
    let length = localStorage.length;
    if(length) {
      for(let i = 0; i < length; i++) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  },

  methods: {
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },

    
    remove(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },

    clear() {
      localStorage.clear();
      this.todoItems = [];
    }
  },
  
  components: {
    'Header': Header,
    'TodoInput': TodoInput,
    'List': List,
    'Clear': Clear
  }

}

</script>

<style>

body {
  text-align: center;
  background-color: seashell;
}

</style>
