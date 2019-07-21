<template>
  <div class="navbar">
    <div class="navtab">
      <i
        v-for="(tab,index) in TAB_LIST"
        :key="index"
        :class="['fas' , getIcon(tab.icon)]"
        @click="$listeners.viewChange(VIEW_STATE.TODOLIST)"
      ></i>
    </div>
    <div class="pomodoro">POMODORO</div>
  </div>
</template>
<script>
import { VIEW_STATE, TAB_LIST } from "../../constant.js";

export default {
  name: "Navbar",
  data() {
    return {
      VIEW_STATE,
      TAB_LIST
    };
  },
  methods: {
    getIcon(icon) {
      switch (icon) {
        case "menu":
          return "fa-bars";
        case "chart":
          return "fa-chart-area";
        case "music":
          return "fa-music";
      }
    }
  }
};
</script>
<style lang="scss" scoped>
.navbar {
  width: 36px;
  height: 700px;
  margin-left: 330px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  .navtab {
    width: 100%;
    height: 204px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    i {
      font-size: 28px;
      color: white;
      cursor: pointer;
    }
  }
  .pomodoro {
    color: white;
    transform: rotate(90deg);
    font-size: 24px;
    font-weight: bold;
    font-family: "roboto";
    margin: 0 0 50px 0;
  }
}
</style>
