<template>
  <div class="mainview">
    <div class="leftview">
      <Dashboard :minutes="minutes" :seconds="seconds" />
    </div>
    <div class="rightview">
      <Navbar />
    </div>
    <play @startTimer="start" />
  </div>
</template>
<script>
import Play from "../components/mainComponents/Play.vue";
import Dashboard from "../components/mainComponents/Dashboard.vue";
import Navbar from "../components/mainComponents/Navbar.vue";

export default {
  name: "Main",
  data: function() {
    return {
      total: 25,
      minutes: 25,
      seconds: 0,
      intervalId: 0
    };
  },
  methods: {
    start: function() {
      let vm = this;
      vm.minutes = vm.total;
      vm.intervalId = setInterval(() => {
        if (vm.seconds % 60 === 0) {
          vm.seconds = vm.minutes * 60;
          vm.minutes--;
        }
        vm.seconds--;
        vm.seconds = vm.seconds % 60;
        console.log(vm.minutes, vm.seconds);
      }, 1000);
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
