<template>
  <div class="navbar">
    <div class="navtab">
      <div class="menu" />
      <div class="chart" />
      <div class="music" />
    </div>
    <div class="pomodoro">POMODORO</div>
  </div>
</template>
<script>
export default {
  name: "Navbar"
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
    div {
      background-repeat: no-repeat;
      background-size: cover;
      width: 28px;
      height: 28px;
      cursor: pointer;

      &.menu {
        background-image: url(../../../public/baseline_menu_white_18dp.png);
      }
      &.chart {
        background-image: url(../../../public/baseline_insert_chart_white_18dp.png);
      }
      &.music {
        background-image: url(../../../public/baseline_library_music_white_18dp.png);
      }
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
