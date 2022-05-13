<template>
  <div>
    <h1 class="titleText">Vue's egna Todo-Lista</h1>
    <TodoList />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import TodoList from "./components/TodoList.vue";
@Options({
  components: {
    TodoList,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
body {
  font-family: "Courier New", Courier, monospace;
  height: 100vh;
  background-color: rgb(204, 204, 204);
  padding: 0px;
  margin: 0px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: rgb(36, 36, 36);
}
.titleText,
.mobileText {
  font-size: 48px;
  text-align: center;
}
</style>
