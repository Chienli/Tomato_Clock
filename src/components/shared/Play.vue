<template>
  <div
    :class="{
      play : true ,
      red_border: !color ,
      blue_border: color,
      size:todoListView
      }"
  >
    <div :class="{
      circle : true ,
      red_bg: !color ,
      blue_bg: color
      }">
      <button
        @click="controlTimer(isPlay)"
        :class="{
          btn:true ,
          btn_stop: isPlay ,
          btn_play: !isPlay,
          red: !color , blue: color ,
          todo_btn_play:todoListView ,
          todo_btn_stop:todoListView 
        }"
      ></button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Play",
  data: function() {
    return {
      isPlay: false
    };
  },
  props: {
    color: {
      type: Boolean
    },
    todoListView: {
      type: Boolean
    }
  },
  methods: {
    controlTimer: function(isPlay) {
      this.isPlay = !this.isPlay;
      this.$emit("handleTimer", !isPlay);
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
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  left: 550px;
  top: 125px;
  .circle {
    width: 520px;
    height: 520px;
    border-radius: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .btn {
    cursor: pointer;
    width: 96px;
    height: 96px;
    background-color: #fff;
    border: none;
    border-radius: 100%;
    outline: none;
    position: relative;
    &::after {
      content: "■";
      color: #ffffff;
      font-size: 20px;
      position: absolute;
      right: -20px;
      bottom: 0px;
    }
  }
  .btn_play {
    &::before {
      content: "▶";
      font-size: 42px;
      position: absolute;
      left: 36px;
      top: 25px;
    }
  }
  .btn_stop {
    &::before {
      content: "=";
      font-size: 80px;
      position: absolute;
      font-weight: bold;
      transform: rotate(90deg);
      left: 24px;
      top: 4px;
    }
  }
}
.red_bg {
  background-color: #ff4384;
}
.blue_bg {
  background-color: #00a7ff;
}
.red_border {
  border: 4px solid #ff4384;
}
.blue_border {
  border: 4px solid #00a7ff;
}
.red {
  color: #ff4384;
}
.blue {
  color: #00a7ff;
}
.size {
  width: 96px;
  height: 96px;
  background-color: #003164;
  position: static;
  left: 0px;
  top: 0px;
  .circle {
    width: 76px;
    height: 76px;
  }
  .btn {
    width: 20px;
    height: 20px;
    background-color: transparent;
    color: white;
    &::after {
      content: "";
    }
  }
  .todo_btn_play:not(.btn_stop) {
    &::before {
      font-size: 36px;
      position: absolute;
      left: 0px;
      top: -8px;
    }
  }
  .todo_btn_stop:not(.btn_play) {
    &::before {
      font-size: 56px;
      position: absolute;
      left: -8px;
      top: -20px;
    }
  }
}
</style>
