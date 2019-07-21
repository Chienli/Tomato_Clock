<template>
  <div class="taskList">
    <div @click="handleFoldState" class="taskList-header">
      <div class="header-title">{{title}}</div>
      <i :class="['fas' , isFold ? 'fa-caret-up' : 'fa-caret-down']"></i>
    </div>
    <div :class="['taskList-body', isFold ? 'hidden' : '']">
      <div v-for="(todo,index) in todos" :key="index" class="list">
        <div
          @click="todo.isCompleted? null : $listeners.isCompletedChange($event,todo.timestamp)"
          class="list-title"
        >
          <!-- <i :class="['fas' , isFold ? 'fa-caret-up' : 'fa-caret-down']"></i> -->
          <i :class="[todo.isCompleted?'fas fa-circle':'far fa-circle']"></i>
          <div :class="[todo.isCompleted?'delete':'']">{{todo.title}}</div>
        </div>
        <i :class="[todo.isCompleted?'':'far fa-caret-square-right']"></i>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "taskList",
  data() {
    return {
      isFold: false
    };
  },
  props: {
    title: String,
    todos: Array
  },
  methods: {
    handleFoldState(e) {
      this.isFold = !this.isFold;
    }
  }
};
</script>
<style lang="scss" scoped>
@mixin text-base {
  color: white;
  font-weight: bold;
}
.taskList {
  .taskList-header {
    width: 445px;
    height: 44px;
    background-color: #335a83;
    line-height: 44px;
    padding: 0 20px;
    margin-bottom: 8px;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    justify-content: space-between;
    cursor: pointer;
    .header-title {
      @include text-base;
      font-family: "roboto";
      font-size: 24px;
    }
    .fas {
      @include text-base;
    }
  }
  width: 445px;
  height: 220px;
  overflow: hidden;
  .taskList-body {
    width: 100%;
    height: 160px;
    overflow-y: scroll;
    box-sizing: content-box;
    padding-right: 22px;
    .list {
      width: 445px;
      height: 32px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      box-sizing: border-box;
      padding: 0 5px;
      @include text-base;
      .list-title {
        display: flex;
        align-items: center;
        font-family: "roboto";
        cursor: pointer;
        i {
          margin-right: 10px;
        }
      }
    }
  }
}
.hidden {
  visibility: hidden;
}
.delete {
  text-decoration: line-through;
}
</style>
