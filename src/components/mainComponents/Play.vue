<template>
  <div class="play">
    <div class="circle">
      <button @click="start"></button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Play",
  methods: {
    start: function() {
      this.$emit("startTimer");
    }
  }
};
</script>
<style lang="scss" scoped>
.play {
  width: 540px;
  height: 540px;
  background-color: transparent;
  border-radius: 100%;
  border: 4px solid #ff4384;
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
  button {
    width: 96px;
    height: 96px;
    background-color: #fff;
    border: none;
    border-radius: 100%;
    outline: none;
    position: relative;
    &::before {
      content: "▶";
      color: #ff4384;
      font-size: 42px;
      position: absolute;
      left: 36px;
      top: 25px;
    }
    &::after {
      content: "■";
      color: #ffffff;
      font-size: 20px;
      position: absolute;
      right: -20px;
      bottom: 0px;
    }
  }
}
</style>
