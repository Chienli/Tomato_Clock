<template>
  <div class="todolistView">
    <div class="inputBox">
      <label for="addTodo">+</label>
      <input class="addTodo" type="text" placeholder="ADD A NEW MISSION…" />
    </div>
    <div class="listBox">
      <div class="listHeader">
        <div class="updown">▲</div>TO-DO
      </div>
      <div class="listBody">
        <div class="list">
          <div class="status">○</div>
          <div>THE FIRST THING TO DO TODAY</div>
          <div class="playBtn">○</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {};
</script>
<style lang="scss" scoped>
.todolistView {
  width: 100%;
  height: 100%;
  background-color: #003164;
  .inputBox {
    width: 445px;
    height: 56px;
    position: relative;
    label[for="addTodo"] {
      position: absolute;
      right: 10px;
      top: 8px;
      color: #ff4384;
      font-family: "roboto";
      font-size: 28px;
    }
    .addTodo {
      width: 100%;
      height: 100%;
      box-sizing: border-box;
      padding: 15px;
      font-weight: bold;
      font-family: "roboto";
      font-style: italic;
      font-size: 16px;
      &::placeholder {
        color: #ff4384;
      }
    }
  }
}
.listHeader {
  width: 455px;
  height: 44px;
  background-color: #335a83;
  color: white;
  box-sizing: border-box;
  padding: 10px;
  font-weight: bold;
  font-family: "roboto";
  font-size: 24px;
  line-height: 22px;
  position: relative;
  .updown {
    font-size: 20px;
    position: absolute;
    right: 15px;
    top: 12px;
  }
  .rotateArrow {
    transform: rotate(180deg);
  }
}
.list {
  width: 445px;
  height: 32px;
  color: white;
  box-sizing: border-box;
  padding: 0 30px;
  font-weight: bold;
  font-family: "roboto";
  font-size: 16px;
  line-height: 16px;
  display: flex;
  align-items: center;
  .status {
    font-size: 50px;
  }
  .playBtn {
    font-size: 50px;
  }
}
</style>

