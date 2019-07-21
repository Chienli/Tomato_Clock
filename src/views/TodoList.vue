<template>
  <div class="todoListView">
    <div class="timerBox">
      <div class="halfCircle">
        <div class="time"></div>
        <div class="playbtnBox"></div>
      </div>
    </div>
<TabList/>
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
import Play from "../components/shared/Play.vue";
import TaskList from "../components/todoListComponents/TaskList.vue";
import TabList from "../components/todoListComponents/TabList.vue";
import { VIEW_STATE } from "../constant.js";

export default {
  name: "todoList",
  data: function() {
    return {
      VIEW_STATE
    };
  },
  props: {
    todos: Array
  },
  computed: {
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
    Play,
    TaskList,
    TabList
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
  .timerBox {
    position: absolute;
    left: 85px;
    bottom: 0px;
    .halfCircle {
      width: 350px;
      height: 175px;
      background-color: #ffedf7;
      border-top-left-radius: 350px;
      border-top-right-radius: 350px;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      .time {
        @include text-base;
        font-size: 64px;
        color: #ff4384;
      }
      .playbtnBox {
        position: absolute;
        top: -60px;
        left: 115px;
        width: 120px;
        height: 120px;
        border-radius: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #003164;
      }
    }
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

