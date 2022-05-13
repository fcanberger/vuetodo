<template>
  <div class="container">
    <TodoCreate @createTodo="handleAddTodo($event)" />
    <TodoTask
      @deleteTask="handleDeletedTask"
      v-for="t in TodoList"
      :key="t"
      :singleTask="t"
    />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import { Todo } from "@/models/todo";
import TodoCreate from "./TodoCreate.vue";
import TodoTask from "./TodoTask.vue";

@Options({
  components: {
    TodoCreate,
    TodoTask,
  },
})
export default class TodoList extends Vue {
  TodoList: Todo[] = [
    new Todo("Sova"),
    new Todo("Stirra in i väggen"),
    new Todo("Pilla naveln"),
  ];

  handleAddTodo(t: Todo) {
    this.TodoList.push(t);
  }
  handleDeletedTask(todo: Todo) {
    this.TodoList.splice(this.TodoList.indexOf(todo), 1);
  }
}
</script>

<style lang="scss">
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
