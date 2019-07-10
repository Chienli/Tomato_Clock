<template>
  <div id="app">
    <!-- <Main /> -->
    <TodoList />
  </div>
</template>

<script>
import Main from "./views/Main.vue";
import TodoList from "./views/TodoList.vue";

export default {
  name: "app",
  components: {
    Main,
    TodoList
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Roboto&display=swap");

#app {
  width: 1280px;
  height: 800px;
  background-color: #eeeeee;
}
</style>
