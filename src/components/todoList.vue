<template>
  <div id="todoList">
    <h1>To Do List</h1>
    <br />
    <h4>You have {{remain}} {{word}}</h4>
    <div v-for="todo in todos" v-bind:key="todo.id">
      <todo v-bind:todo="todo" v-on:remove="$emit('remove',todo.id)" />
    </div>
    <div>
      <input type="text" placeholder="Add todos" v-model="title" />
      <button v-on:click="addTodo(title)">Create</button>
    </div>
  </div>
</template>

<script>
import todo from "./todoItem.vue";

export default {
  components: {
    todo: todo
  },
  props: {
    todos: Array
  },

  data: () => ({
    title: ""
  }),

  methods: {
    addTodo(title) {
      const newTodo = {
        id: Date.now(),
        title,
        done: false
      };
      if (this.title !== "") {
        this.$emit("newItem", newTodo);
        this.title = "";
      }
    }
  },

  computed: {
    remain() {
      var i = this.todos.filter(todo => !todo.done).length;
      return i;
    },
    word() {
      var i = this.todos.filter(todo => !todo.done).length;
      if (i <= 1) {
        return "todo";
      } else {
        return "todos";
      }
    }
  }
};
</script>

<style>
</style>