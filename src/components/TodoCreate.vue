<template>
  <form class="createContainer" @submit.prevent="onSubmit">
    <input
      type="text"
      placeholder="Write a description"
      v-model="description"
    />
    <button class="btn btn--save" @click="addTodo">Save</button>
  </form>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Todo } from "@/models/todo";
import { Prop } from "vue-property-decorator";

export default class TodoCreate extends Vue {
  @Prop() saveBtn!: string;
  description = "";

  addTodo() {
    this.$emit("TodoCreate", new Todo(this.description));
    this.description = "";
  }
}
</script>

<style lang="scss" scoped>
input {
  border: none;
  border-radius: 5px;
  background-color: rgb(139, 139, 139);
  height: 50px;
  width: 250px;
  text-align: center;
}
.btn--save {
  background-color: #1100ff;
  width: 25px;
  height: 25px;
}
.btn {
  height: 50px;
  width: 100px;
}
.createContainer {
  display: flex;
  gap: 15px;
  margin-bottom: 25px;
}
</style>
