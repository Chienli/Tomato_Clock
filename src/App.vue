<template>
  <div id="app">
    <Main v-if="viewState === 0" :todos="todos" @handleViewState="handleViewState" />
    <TodoList
      v-else-if="viewState === 1"
      :todos="todos"
      :done="done"
      @handleViewState="handleViewState"
    />
  </div>
</template>

<script>
import Main from "./views/Main.vue";
import TodoList from "./views/TodoList.vue";
export default {
  name: "app",
  methods: {
    handleViewState: function(state) {
      this.viewState = state;
    }
  },
  data: function() {
    return {
      todos: [
        {
          title: "THE FIRST THING TO DO TODAY",
          date: new Date().getTime()
        },
        {
          title: "THE Second THING TO DO TODAY",
          date: new Date().getTime()
        },
        {
          title: "THE Third THING TO DO TODAY",
          date: new Date().getTime()
        }
      ],
      done: [
        {
          title: "aaaa",
          date: new Date().getTime()
        },
        {
          title: "bbbb",
          date: new Date().getTime()
        },
        {
          title: "ccc",
          date: new Date().getTime()
        }
      ],
      viewState: 0
    };
  },
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
