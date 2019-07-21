<template>
  <div class="mainview">
    <div class="leftview">
      <Dashboard
        @viewChange="$listeners.viewChange"
        :todos="todos"
        @addTodo="$listeners.addTodo"
        :displayTime="displayTime"
      />
    </div>
    <div class="rightview">
      <Navbar @viewChange="$listeners.viewChange" />
    </div>
    <Play :isPlay="isPlay" @isPlayChange="$listeners.isPlayChange" />
  </div>
</template>
<script>
import Play from "../components/mainComponents/Play.vue";
import Dashboard from "../components/mainComponents/Dashboard.vue";
import Navbar from "../components/mainComponents/Navbar.vue";

export default {
  name: "Main",
  methods: {},
  props: {
    todos: Array,
    displayTime: String,
    isPlay: Boolean
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
