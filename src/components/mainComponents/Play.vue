<template>
  <div class="play">
    <div class="circle">
      <div class="btn">
        <i :class="['fas',isPlay?'fa-equals':'fa-play']" @click="$listeners.isPlayChange" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Play",
  props: {
    isPlay: Boolean
  }
};
</script>

<style lang="scss" scoped>
@mixin btn-base {
  cursor: pointer;
  font-size: 32px;
  text-align: center;
  color: #ff4384;
  position: absolute;
  left: 35px;
}
@mixin center-circle {
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 100%;
}
.play {
  width: 540px;
  height: 540px;
  background-color: transparent;
  border: 4px solid #ff4384;
  position: absolute;
  left: 550px;
  top: 125px;
  @include center-circle;
  .circle {
    width: 520px;
    height: 520px;
    background-color: #ff4384;
    @include center-circle;
  }
  .btn {
    width: 96px;
    height: 96px;
    background-color: #fff;
    @include center-circle;
    position: relative;
    &::after {
      content: "■";
      color: #ffffff;
      font-size: 20px;
      position: absolute;
      right: -20px;
      bottom: 0px;
    }
    .fa-play {
      @include btn-base;
    }
    .fa-equals {
      @include btn-base;
      transform: rotate(90deg);
    }
  }
}
</style>
