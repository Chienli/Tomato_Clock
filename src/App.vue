<template>
  <div id="app">
    <Main
      :minutes="minutes"
      :seconds="seconds"
      :intervalId="intervalId"
      :todos="todos"
      :timerColor="timerColor"
      :isPlay="isPlay"
      @handleViewState="handleViewState"
      @handleTimer="handleTimer"
      v-if="viewState === 0"
    />
    <TodoList
      :minutes="minutes"
      :seconds="seconds"
      :intervalId="intervalId"
      :timerColor="timerColor"
      :todos="todos"
      :done="done"
      :isPlay="isPlay"
      @handleTimer="handleTimer"
      @handleViewState="handleViewState"
      v-else-if="viewState === 1"
    />
  </div>
</template>

<script>
import Main from "./views/Main.vue";
import TodoList from "./views/TodoList.vue";
export default {
  name: "app",
  data: function() {
    return {
      todos: [],
      done: [],
      viewState: 0,
      minutes: 5,
      seconds: 0,
      intervalId: 0,
      isPlay: false
    };
  },
  methods: {
    handleTimer: function(isPlay) {
      this.isPlay = isPlay;
      if (isPlay) {
        let vm = this;
        vm.intervalId = setInterval(() => {
          if (vm.seconds % 60 === 0) {
            vm.seconds = vm.minutes * 60;
            vm.minutes--;
          }
          vm.seconds--;
          vm.seconds = vm.seconds % 60;
        }, 1000);
      } else {
        window.clearInterval(this.intervalId);
      }
    },
    handleViewState: function(state) {
      this.viewState = state;
    }
  },
  computed: {
    timerColor: function() {
      if (this.minutes <= 4) {
        return true;
      } else {
        return false;
      }
    },
    stopTimer: function() {
      if (this.minutes === 0 && this.seconds === 0) {
        window.clearInterval(this.intervalId);
        return "the timer is stop";
      } else {
        return "Not yet";
      }
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

#app {
  width: 1280px;
  height: 800px;
  background-color: #eeeeee;
}
</style>
