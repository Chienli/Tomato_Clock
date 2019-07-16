<template>
  <div class="mainview">
    <div class="leftview" :style="{background: timerColor ? '#E5F3FF' : '#FFEDF7'}">
      <Dashboard :minutes="minutes" :seconds="seconds" :color="timerColor" :todos="todos" />
    </div>
    <div class="rightview">
      <Navbar @handleViewState="handleViewState" />
    </div>
    <play :isPlay="isPlay" @handleTimer="handleTimer" :color="timerColor" />
  </div>
</template>
<script>
import Play from "../components/shared/Play.vue";
import Dashboard from "../components/mainComponents/Dashboard.vue";
import Navbar from "../components/mainComponents/Navbar.vue";

export default {
  name: "Main",
  methods: {
    handleViewState: function(state) {
      this.$emit("handleViewState", state);
    },
    handleTimer: function(isplay) {
      this.$emit("handleTimer", isplay);
    }
  },
  props: {
    todos: {
      type: Array
    },
    minutes: {
      type: Number
    },
    seconds: {
      type: Number
    },
    intervalId: {
      type: Number
    },
    isPlay: {
      type: Boolean
    },
    timerColor: {
      type: Boolean
    }
  },
  components: {
    Play,
    Dashboard,
    Navbar
  }
};
</script>
<style lang="scss" scoped>
.mainview {
  width: 100%;
  height: 100%;
  display: flex;
  position: relative;
  .leftview {
    width: 830px;
    height: 100%;
    background-color: #ffedf7;
  }
  .rightview {
    width: 450px;
    height: 100%;
    background-color: #003164;
    display: flex;
    align-items: center;
  }
}
</style>
