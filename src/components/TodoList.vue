<template lang="html">
  <div>
    <p>Completed Tasks: {{ todos.filter(todo => todo.done === true).length }}</p>
    <p>Pending Tasks: {{ todos.filter(todo => todo.done === false).length }}</p>
    <todo v-on:complete-todo="completeTodo" v-on:delete-todo="deleteTodo" v-for="(todo, index) in todos" v-bind:todo="todo" :key="index"></todo>
  </div>
</template>

<script>
import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
  },
};
</script>

<style lang="css">
</style>
