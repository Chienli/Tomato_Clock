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
    <div class="listbox">
      <div class="list">THE SECOND THING TO DO TODAY</div>
      <div class="list">THE THIRD THING TO DO TODAY</div>
      <div class="list">THE FORTH THING TO DO TODAY</div>
      <div class="more" :style="{color : color? '#00A7FF':'#ff4384'}">MORE</div>
    </div>
  </div>
</template>
<script>
import AddNewMission from "../shared/AddNewMission.vue";

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
  .listbox {
    width: 445px;
    height: 112px;
    color: #003164;
    font-weight: bold;
    font-size: 16px;
    font-family: "roboto";
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    position: relative;
    .list {
      cursor: pointer;
      width: 100%;
      height: 32px;
      border-bottom: 1px solid #cccccc;
      line-height: 32px;
      padding: 0 25px;
      position: relative;
      box-sizing: border-box;
      &::before {
        content: "○";
        font-size: 35px;
        position: absolute;
        left: 0px;
        top: -3px;
      }
      &::after {
        content: "▶";
        position: absolute;
        right: 0px;
        border-radius: 100%;
        border: #003164 solid 2px;
        width: 20px;
        height: 20px;
        text-align: center;
        font-size: 12px;
        padding-left: 2px;
        line-height: 18px;
        box-sizing: border-box;
      }
    }
    .more {
      position: absolute;
      color: #ff4384;
      font-weight: bold;
      font-size: 14px;
      bottom: -28px;
      right: 0px;
      cursor: pointer;
    }
  }
}

</style>
