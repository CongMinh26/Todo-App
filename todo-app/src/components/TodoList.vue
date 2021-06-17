<template>
  <div>
    <h3>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</h3>
  
    <h3>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</h3>

    <todo  v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" v-bind:todo="todo" :key="todo"></todo>

  </div>
</template>

<script type = "text/javascript" >

import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods:{
    deleteTodo(todo){
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex,1)
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
  }
};
</script>
<style >

</style>