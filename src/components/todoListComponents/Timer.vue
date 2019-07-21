<template>
  <div class="timerBox">
    <div class="halfCircle">
      <div class="time">{{displayTime}}</div>
      <div class="playbtnBox">
        <!-- duplicated far -->
        <i
          :class="[isPlay?'far fa-stop-circle':'far fa-play-circle']"
          @click="$listeners.isPlayChange"
        ></i>
      </div>
      <div class="title">{{todos[0] && todos[0].title}}</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "timer",
  props: {
    displayTime: String,
    isPlay: Boolean,
    todos: Array
  }
};
</script>
<style lang="scss" scoped>
@mixin text-base {
  font-family: "roboto";
  font-weight: bold;
  color: white;
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
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .time {
      @include text-base;
      font-size: 64px;
      color: #ff4384;
      margin-top: 30px;
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
      i {
        font-size: 110px;
        color: #ffedf7;
        cursor: pointer;
      }
    }
    .title{
        @include text-base;
        color: #003164;
    }
  }
}
</style>
