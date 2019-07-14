<template>
  <div class="dashboard">
    <AddNewMission :color="color" />
    <div class="timebox">
      <div>THE FIRST THING TO DO TODAY</div>
      <div
        v-if="seconds < 10 && minutes >= 10"
        :style="{color : color? '#00A7FF':'#ff4384'}"
      >{{minutes + ":0" + seconds}}</div>
      <div
        v-else-if="seconds < 10 && minutes < 10"
        :style="{color : color?'#00A7FF':'#ff4384'}"
      >{{ "0" + minutes + ":0" + seconds}}</div>
      <div
        v-else-if="seconds >= 10 && minutes < 10"
        :style="{color : color?'#00A7FF':'#ff4384'}"
      >{{ "0" + minutes + ":" + seconds}}</div>
      <div
        v-else-if="seconds >= 10  && minutes >= 10"
        :style="{color : color?'#00A7FF':'#ff4384'}"
      >{{minutes + ":" + seconds}}</div>
    </div>
    <TaskListBox :todos="todos" />
  </div>
</template>
<script>
import AddNewMission from "../shared/AddNewMission.vue";
import TaskListBox from "../shared/TaskListBox.vue";
export default {
  name: "Dashboard",
  props: {
    minutes: {
      type: Number
    },
    seconds: {
      type: Number
    },
    color: {
      type: Boolean
    },
    todos: {
      type: Array
    }
  },
  components: {
    AddNewMission,
    TaskListBox
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
          font-weight: normal;
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
}
</style>
