<template>
  <div class="navbar">
    <div class="navtab">
      <!-- list render -->
      <i @click="$listeners.viewChange(VIEW_STATE.TODOLIST)" class="fas fa-bars"></i>
      <i @click="$listeners.viewChange(VIEW_STATE.TODOLIST)" class="fas fa-chart-area"></i>
      <i @click="$listeners.viewChange(VIEW_STATE.TODOLIST)" class="fas fa-music"></i>
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
