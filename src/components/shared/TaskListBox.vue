<template>
  <div class="listbox">
    <div
      class="list"
      v-for="(todo,index) in todos"
      :key="index"
      :style="{color:isThisView ? '#ffffff' : '#003164'}"
    >{{todo.title}}</div>
    <div v-if="viewState !== 1" class="more" :style="{color : color? '#00A7FF':'#ff4384'}">MORE</div>
  </div>
</template>
<script>
export default {
  name: "taskListBox",
  props: {
    color: {
      type: Boolean
    },
    todos: {
      type: Array
    },
    viewState: {
      type: Number
    }
  },
  computed: {
    isThisView: function() {
      if (this.viewState === 1) {
        return true;
      } else {
        return false;
      }
    }
  }
};
</script>
<style lang="scss">
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
    cursor: pointer;
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
    cursor: pointer;
  }
}
</style>


