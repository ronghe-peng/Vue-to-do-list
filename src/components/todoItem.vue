<template>
  <div class="todoItem" :class="{finish: todo.done}">
    <div class="todo">
      <input type="checkbox" v-on:change="done" />
      <p
        contenteditable="true"
        spellcheck="false"
        v-on:keydown.enter="updateTodo($event, todo)"
        v-on:blur="updateTodo($event, todo)"
      >{{todo.title}}</p>
    </div>
    <button v-on:click="$emit('remove',todo.id)">Delete</button>
  </div>
</template>

<script>
export default {
  props: {
    todo: Object
  },

  methods: {
    done() {
      this.todo.done = !this.todo.done;
    },
    updateTodo(e, todo) {
      e.preventDefault();
      todo.title = e.target.innerText;
      e.target.blur();
    }
  }
};
</script>

<style>
input {
  font-size: 14px;
  padding: 0.5rem;
}
button {
  padding: 0.5rem;
  font-size: 16px;
  margin: 0.5rem;
}
div {
  margin: auto;
  text-align: center;
}
.todo {
  display: flex;
  align-items: center;
  margin-left: 1rem;
}
.todoItem {
  justify-content: space-between;
  border: 1px solid black;
  display: flex;
  margin: 0.5rem;
}
.finish p {
  text-decoration: line-through;
  color: gray;
}
p {
  margin: 0.5rem;
}
</style>