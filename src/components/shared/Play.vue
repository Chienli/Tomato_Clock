<template>
  <div class="play">
    <div class="circle">
      <div class="btn">
        <i class="fas fa-play" v-if="!isPlay" @click="$listeners.isPlayChange" />
        <i class="fas fa-equals" v-else-if="isPlay" @click="$listeners.isPlayChange" />
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
.play {
  width: 540px;
  height: 540px;
  background-color: transparent;
  border: 4px solid #ff4384;
  border-radius: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  left: 550px;
  top: 125px;
  .circle {
    width: 520px;
    height: 520px;
    background-color: #ff4384;
    border-radius: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .btn {
    width: 96px;
    height: 96px;
    background-color: #fff;
    border: none;
    border-radius: 100%;
    outline: none;
    display: flex;
    align-items: center;
    justify-content: center;
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
      cursor: pointer;
      font-size: 32px;
      text-align: center;
      color: #ff4384;
    }
    .fa-equals {
      cursor: pointer;
      font-size: 32px;
      transform: rotate(90deg);
      text-align: center;
      color: #ff4384;
    }
  }
}
</style>
