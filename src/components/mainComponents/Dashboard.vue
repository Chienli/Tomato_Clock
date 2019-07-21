<template>
  <div class="dashboard">
    <AddNewMission @addTodo="$listeners.addTodo" />
    <div class="timebox">
      <div>{{uncompletedtodos[0] ? uncompletedtodos[0].title : "YOU DON'T HAVE TASK TO DO"}}</div>
      <div>{{displayTime}}</div>
    </div>
    <div class="taskListBox">
      <div class="taskList">
        <div v-for="(todo,index) in uncompletedtodos" :key="index" class="list">
          <div class="list-title">
            <i class="far fa-circle"></i>
            <div>{{todo.title}}</div>
          </div>
          <i class="far fa-caret-square-right"></i>
        </div>
      </div>
      <div
        v-if="uncompletedtodos.length !== 0"
        @click="$listeners.viewChange(VIEW_STATE.TODOLIST)"
        class="more"
      >MORE</div>
    </div>
  </div>
</template>
<script>
import AddNewMission from "../shared/AddNewMission.vue";
import { VIEW_STATE } from "../../constant.js";

export default {
  name: "Dashboard",
  data() {
    return {
      VIEW_STATE
    };
  },
  props: {
    displayTime: String,
    todos: Array
  },
  computed: {
    // extract it into utils
    uncompletedtodos() {
      return _.filter(this.todos, todo => {
        return !todo.isCompleted;
      });
    }
  },
  components: {
    AddNewMission
  }
};
</script>
<style lang="scss" scoped>
.dashboard {
  width: 454px;
  height: 100%;
  margin-left: 80px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  .timebox {
    position: relative;
    div {
      &:nth-child(1) {
        color: #003164;
        font-weight: bold;
        font-size: 20px;
        font-family: "roboto";
        position: absolute;
        left: 64px;
        top: -40px;
        &::before {
          content: "○";
          position: absolute;
          bottom: -20px;
          color: #ff4384;
        }
        &::after {
          content: "○";
          position: absolute;
          font-size: 100px;
          left: -65px;
          top: -45px;
        }
      }
      &:nth-child(2) {
        color: #ff4384;
        font-weight: bold;
        font-size: 176px;
        font-family: "roboto";
      }
    }
  }
  .taskListBox {
    position: relative;
    .taskList {
      width: 445px;
      height: 114px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      overflow: hidden;
      .list {
        height: 32px;
        font-weight: bold;
        color: #003164;
        font-family: "roboto";
        border-bottom: 1px solid #aaaaaa;
        width: 100%;
        box-sizing: border-box;
        display: flex;
        align-self: center;
        justify-content: space-between;
        margin-top: 6px;
        i {
          line-height: 32px;
        }
        .list-title {
          display: flex;
          align-items: center;
          i {
            margin-right: 10px;
          }
        }
      }
    }
    .more {
      bottom: -25px;
      right: 0;
      position: absolute;
      font-weight: bold;
      color: #ff4384;
      font-family: "roboto";
      z-index: 1;
    }
  }
}
</style>
