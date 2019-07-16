<template>
  <div class="listbox">
    <div :class="{list:true , color_white:todoListView}" v-for="(todo,index) in todos" :key="index">
      {{todo.title}}
      <div :class="{playbtn:true  , border_color_white:todoListView}">▶</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "taskListBox",
  props: {
    todoListView: {
      type: Boolean
    },
    todos: {
      type: Array
    }
  }
};
</script>
<style lang="scss">
.listbox {
  width: 445px;
  height: 128px;
  color: #003164;
  font-weight: bold;
  font-size: 16px;
  font-family: "roboto";
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  position: relative;
  overflow-y: auto;
  .list {
    cursor: pointer;
    width: 100%;
    height: 32px;
    border-bottom: 1px solid #cccccc;
    line-height: 32px;
    margin-bottom: 9px;
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
    .playbtn {
      box-sizing: border-box;
      position: absolute;
      width: 24px;
      height: 24px;
      font-size: 14px;
      text-align: center;
      line-height: 20px;
      top: 0px;
      right: 0px;
      border-width: 2px;
      border-color: #003164;
      border-style: solid;
      border-radius: 100%;
    }
  }
}
.color_white {
  color: white;
}
.border_color_white {
  border-color: white !important ;
}
</style>
