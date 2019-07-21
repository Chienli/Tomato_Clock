<template>
  <div class="todoListView">
    <div class="timerBox">
      <div class="halfCircle">
        <div class="time"></div>
        <div class="playbtnBox"></div>
      </div>
    </div>
    <div class="tabListBox">
      <div :key="index" v-for="(tab,index) in TAB_LIST" class="tabList">
        <div :class="[tab.icon]"></div>
        <div>{{tab.title}}</div>
      </div>
    </div>
    <div class="listColumn">
      <AddNewMission @addTodo="$listeners.addTodo" />
      <TaskList
        :title="'TODO'"
        :todos="uncompletedtodos"
        @isCompletedChange="$listeners.isCompletedChange"
      />
      <TaskList  :title="'DONE'" :todos="completedtodos" />
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
import { VIEW_STATE, TAB_LIST } from "../constant.js";

export default {
  name: "todoList",
  data: function() {
    return {
      TAB_LIST,
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
    TaskList
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
  .tabListBox {
    height: 700px;
    .tabList {
      width: 236px;
      height: 42px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin: 42px 0;
      cursor: pointer;
      img {
        width: 36px;
        height: 36px;
      }
      div:nth-child(1) {
        width: 32px;
        height: 32px;
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        &.menu {
          background-image: url(../../public/menu_pink.png);
        }
        &.chart {
          background-image: url(../../public/chart_pink.png);
        }
        &.music {
          background-image: url(../../public/music_pink.png);
        }
      }
      div:nth-child(2) {
        @include text-base;
        width: 192px;
        font-size: 36px;
        text-align: left;
        color: #ff4384;
      }
    }
  }
}
</style>

