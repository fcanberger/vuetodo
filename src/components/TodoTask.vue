<template>
  <div class="container">
    <div class="taskCont">
      <p :class="{ statusText: singleTask.done }">
        {{ singleTask.description }}
      </p>
      <button
        class="btn btn--change"
        @click="changeStatus"
        v-if="singleTask.done"
      >
        Inte klar
      </button>
      <button class="btn btn--change" @click="changeStatus" v-else>Klar</button>
      <button
        class="btn btn--delete"
        @click="
          () => {
            handleDeleteTask();
          }
        "
      >
        Radera
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Todo } from "@/models/todo";
import { Prop } from "vue-property-decorator";

export default class TodoCreate extends Vue {
  @Prop() singleTask!: Todo;
  changeStatus() {
    this.singleTask.done = !this.singleTask.done;
  }
  handleDeleteTask() {
    this.$emit("deleteTask", this.singleTask);
  }
}
</script>

<style lang="scss">
.btn--change {
  background-color: #1ed760;
  width: 50px;
  height: 50px;
  box-shadow: 5px 2.5px 2.5px black;
}
.btn--delete {
  background-color: rgb(145, 2, 2);
  width: 50px;
  height: 50px;
  box-shadow: 5px 2.5px 2.5px black;
}
.btn {
  border: none;
  color: white;
  height: 50px;
  width: 100px;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 5px 2.5px 2.5px black;
  &:hover {
    transform: scale(1.05);
  }
}
.taskCont {
  display: flex;
  gap: 15px;
  font-size: 24px;
  align-items: left;
}
.statusText {
  text-decoration: line-through;
}
</style>
