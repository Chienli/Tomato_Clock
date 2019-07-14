<template>
  <div class="inputBox">
    <label for="addNewMission" :style="{color : color? '#00A7FF':'#ff4384'}">+</label>
    <input
      type="text"
      id="addNewMission"
      placeholder="ADD A NEW MISSION…"
      :class="{red: !color , blue: color }"
    />
  </div>
</template>
<script>
export default {
  name: "addNewMission",
  props: {
    color: {
      type: Boolean
    }
  }
};
</script>
<style lang="scss" >
.inputBox {
  position: relative;
  label[for="addNewMission"] {
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
    font-weight: bold;
    font-size: 18px;
    font-style: italic;
    &::placeholder {
      font-family: "roboto";
      font-weight: bold;
      font-style: italic;
      font-size: 16px;
    }
  }
}
.red {
  &::placeholder {
    color: #ff4384;
  }
}
.blue {
  &::placeholder {
    color: #00a7ff;
  }
}
</style> 
