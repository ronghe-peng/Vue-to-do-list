<template>
  <!--run project: 'npm run serve'-->
  <div id="app">
    <todos v-bind:todos="todos" v-on:newItem="addTodo" v-on:remove="removetodo" />
  </div>
</template>

<script>
import todos from "./components/todoList.vue";

export default {
  components: {
    todos: todos
  },
  data: () => ({
    todos: []
  }),
  methods: {
    addTodo(newTodo) {
      this.todos.push(newTodo);
    },
    removetodo(id) {
      this.todos = this.todos.filter(mytodo => {
        return mytodo.id !== id;
      });
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

#app {
  width: 80%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>