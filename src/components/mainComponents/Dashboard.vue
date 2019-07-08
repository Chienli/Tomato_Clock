<template>
  <div class="dashboard">
    <div class="inputBox">
      <label for="addNewMission">+</label>
      <input type="text" id="addNewMission" placeholder="ADD A NEW MISSION…" />
    </div>
    <div class="timebox">
      <div>THE FIRST THING TO DO TODAY</div>
      <div>25:00</div>
    </div>
    <div class="listbox">
      <div class="list">THE SECOND THING TO DO TODAY</div>
      <div class="list">THE THIRD THING TO DO TODAY</div>
      <div class="list">THE FORTH THING TO DO TODAY</div>
      <div class="more">MORE</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Dashboard"
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
  .inputBox {
    position: relative;
    label[for="addNewMission"] {
      color: #ff4384;
      font-size: 26px;
      font-family: "roboto";
      position: absolute;
      right: 20px;
      top: 12px;
    }
    #addNewMission {
      width: 445px;
      height: 56px;
      box-sizing: border-box;
      padding: 0 15px;
      outline: none;
      border: none;
      color: #ff4384;
      font-weight: bold;
      font-size: 18px;
      font-style: italic;
      &::placeholder {
        font-family: "roboto";
        color: #ff4384;
        font-weight: bold;
        font-style: italic;
        font-size: 16px;
      }
    }
  }
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
    }
  }
}
</style>
