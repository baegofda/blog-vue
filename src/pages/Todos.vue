<template>
  <main class="wrapper">
    <h1 class="title">TODO</h1>
    <form class="form">
      <input
        ref="todoInput"
        type="text"
        class="form--input"
        placeholder="추가할 리스트를 입력하여 주세요 !"
        v-model="inputText"
      />
      <Button type="submit" name="추가하기" @click="onClick" />
    </form>
    <ul>
      <ToDoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @onComplete="onComplete($event)"
        @onDelete="onDelete($event)"
      />
    </ul>
  </main>
</template>

<script>
import Button from "../components/Button.vue";
import ToDoItem from "../components/ToDoItem.vue";

export default {
  name: "Todos",
  data() {
    return {
      inputText: "",
      todos: [
        {
          id: Date.now(),
          content: "hhh",
          isCompleted: false,
        },
      ],
    };
  },
  methods: {
    onClick(e) {
      e.preventDefault();
      const todo = {
        id: Date.now(),
        content: this.inputText,
        isCompleted: false,
      };
      this.todos = [...this.todos, todo];
      this.inputText = "";
      this.$refs.todoInput.focus();
    },
    onComplete(id) {
      this.todos = this.todos.map((todo) => {
        if (todo.id === id) {
          return { ...todo, isCompleted: !todo.isCompleted };
        }
        return todo;
      });
    },
    onDelete(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
  },
  components: {
    Button,
    ToDoItem,
  },
};
</script>

<style>
.wrapper {
  padding-top: 150px;
}
.title {
  margin-bottom: 50px;
  font-size: 30px;
  font-weight: 700;
  text-align: center;
}
.form {
  display: flex;
  width: 400px;
  height: 40px;
  margin-bottom: 20px;
}
.form--input {
  margin-right: 5px;
  background-color: transparent;
  border: 0;
  outline: 0;
  border-bottom: 1px solid rgba(0, 0, 0, 0.7);
  flex: 1;
}
</style>
