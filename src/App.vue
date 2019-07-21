<template>
  <div id="app">
    <div class="container">
      <Main
        v-if="viewState === VIEW_STATE.MAIN"
        :displayTime="displayTime"
        :todos="todos"
        :isPlay="isPlay"
        @viewChange="handleViewState"
        @isPlayChange="toggleTimer"
        @addTodo="addTodo"
      />
      <TodoList
        :todos="todos"
        @isCompletedChange="handleCompleted"
        @viewChange="handleViewState"
        @addTodo="addTodo"
        :isPlay="isPlay"
        @isPlayChange="toggleTimer"
        :displayTime="displayTime"
        v-else-if="viewState === VIEW_STATE.TODOLIST"
      />
    </div>
  </div>
</template>

<script>
import numeral from "numeral";
import Main from "./views/Main.vue";
import { VIEW_STATE } from "./constant.js";
import TodoList from "./views/TodoList.vue";
import _ from "lodash";
export default {
  name: "app",
  data: function() {
    return {
      todos: [],
      remains: 1500,
      viewState: 0,
      isPlay: false,
      VIEW_STATE
    };
  },
  methods: {
    countDown() {
      // setInterval
      if (this.remains > 0 && this.isPlay) {
        this.remains -= 1;
        setTimeout(this.countDown, 1000);
      }
    },
    toggleTimer() {
      this.isPlay = !this.isPlay;
      this.isPlay && this.countDown();
    },
    handleViewState: function(state) {
      this.viewState = state;
    },
    addTodo(e) {
      this.todos.push({
        title: e.target.value,
        timestamp: new Date().getTime(),
        isCompleted: false
      });
      e.target.value = "";
    },
    handleCompleted(e, timestamp) {
      // const
      let newTodos = _.cloneDeep(this.todos);
      _.set(
        _.find(newTodos, todo => {
          return todo.timestamp == timestamp;
        }),
        "isCompleted",
        true
      );
      this.todos = newTodos;
    }
  },
  computed: {
    displayTime: function() {
      const { remains } = this;
      const minute = numeral(Math.floor(remains / 60)).format("00");
      const second = numeral(remains % 60).format("00");
      return `${minute}:${second}`;
    }
  },
  components: {
    Main,
    TodoList
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Roboto&display=swap");
body {
  margin: 0px;
}
#app {
  width: 100%;
  height: 100vh;
  background-color: #eeeeee;
  display: flex;
  align-items: center;
  justify-content: center;
  .container {
    width: 1280px;
    height: 800px;
  }
}
</style>
