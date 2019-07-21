<template>
  <div class="todoListView">
    <Timer
      :todos="uncompletedtodos"
      :displayTime="displayTime"
      :isPlay="isPlay"
      @isPlayChange="$listeners.isPlayChange"
    />
    <TabList />
    <div class="listColumn">
      <AddNewMission @addTodo="$listeners.addTodo" />
      <TaskList
        :title="'TODO'"
        :todos="uncompletedtodos"
        @isCompletedChange="$listeners.isCompletedChange"
      />
      <TaskList :title="'DONE'" :todos="completedtodos" />
    </div>
    <div class="navbar">
      <div @click="$listeners.viewChange(VIEW_STATE.MAIN)" class="cross">✖</div>
      <div class="pomodoro">POMODORO</div>
    </div>
  </div>
</template>
<script>
import _ from "lodash";
import AddNewMission from "../components/shared/AddNewMission.vue";
import TaskList from "../components/todoListComponents/TaskList.vue";
import TabList from "../components/todoListComponents/TabList.vue";
import Timer from "../components/todoListComponents/Timer.vue";
import { VIEW_STATE } from "../constant.js";

export default {
  name: "todoList",
  data: function() {
    return {
      VIEW_STATE
    };
  },
  props: {
    todos: Array,
    displayTime: String,
    isPlay: Boolean
  },
  computed: {
    // extract it into utils
    uncompletedtodos() {
      return _.filter(this.todos, todo => {
        return !todo.isCompleted;
      });
    },
    completedtodos() {
      return _.filter(this.todos, todo => {
        return todo.isCompleted;
      });
    }
  },
  components: {
    AddNewMission,
    TaskList,
    TabList,
    Timer
  }
};
</script>
<style lang="scss" scoped>
@mixin text-base {
  font-family: "roboto";
  font-weight: bold;
  color: white;
}
.todoListView {
  width: 100%;
  height: 100%;
  background-color: #003164;
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: relative;
  .listColumn {
    width: 455px;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
  }
  .navbar {
    width: 36px;
    height: 700px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    .cross {
      font-size: 30px;
      display: flex;
      flex-direction: column;
      align-items: center;
      cursor: pointer;
      @include text-base;
    }
    .pomodoro {
      transform: rotate(90deg);
      font-size: 24px;
      margin: 0 0 50px 0;
      @include text-base;
    }
  }
}
</style>

