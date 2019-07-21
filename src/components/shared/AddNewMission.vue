<template>
  <div class="inputBox">
    <label for="addNewMission" >+</label>
    <input @keyup.enter="$listeners.addTodo" type="text" id="addNewMission" placeholder="ADD A NEW MISSION…" />
  </div>
</template>
<script>
export default {
  name: "addNewMission"
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
    cursor: pointer;
    color: #ff4384;
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
      color: #ff4384;
    }
  }
}
</style> 
