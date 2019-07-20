<template>
  <div class="navbar">
    <div class="navtab">
      <div class="menu" @click="$listeners.viewChange(VIEW_STATE.TODOLIST)" />
      <div class="chart" @click="$listeners.viewChange(VIEW_STATE.TODOLIST)" />
      <div class="music" @click="$listeners.viewChange(VIEW_STATE.TODOLIST)" />
    </div>
    <div class="pomodoro">POMODORO</div>
  </div>
</template>
<script>
import { VIEW_STATE } from "../../constant.js";

export default {
  name: "Navbar",
  data() {
    return {
      VIEW_STATE
    };
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
    div {
      width: 28px;
      height: 28px;
      cursor: pointer;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      &.menu {
        background-image: url(../../../public/menu_white.png);
      }
      &.chart {
        background-image: url(../../../public/chart_white.png);
      }
      &.music {
        background-image: url(../../../public/music_white.png);
      }
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
