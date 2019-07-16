<template>
  <div class="todoListView">
    <div class="timerBox">
      <div class="halfCircle">
        <div class="time">
          <div v-if="seconds < 10 && minutes >= 10">{{minutes + ":0" + seconds}}</div>
          <div v-else-if="seconds < 10 && minutes < 10">{{ "0" + minutes + ":0" + seconds}}</div>
          <div v-else-if="seconds >= 10 && minutes < 10">{{ "0" + minutes + ":" + seconds}}</div>
          <div v-else-if="seconds >= 10  && minutes >= 10">{{minutes + ":" + seconds}}</div>
        </div>
        <div class="playbtnBox">
          <Play :isPlay="isPlay" @handleTimer="handleTimer" class="playbtn" :todoListView="true" />
        </div>
      </div>
    </div>
    <div class="listColumn">
      <AddNewMission :color="false" />
      <div>
        <ListHeader :title="'TODO'" :foldState="todoFoldState" @handleFold="handleFold" />
        <TaskListBox :class="{hidden : todoFoldState}" :todoListView="true" :todos="todos" />
      </div>
      <div>
        <ListHeader :title="'DONE'" :foldState="doneFoldState" @handleFold="handleFold" />
        <TaskListBox :class="{hidden : doneFoldState}" :todoListView="true" :todos="done" />
      </div>
    </div>
  </div>
</template>
<script>
import AddNewMission from "../components/shared/AddNewMission.vue";
import TaskListBox from "../components/shared/TaskListBox.vue";
import ListHeader from "../components/todoListComponents/ListHeader.vue";
import Play from "../components/shared/Play.vue";

export default {
  name: "todoList",
  data: function() {
    return {
      todoFoldState: false,
      doneFoldState: false
    };
  },
  props: {
    todos: {
      type: Array
    },
    done: {
      type: Array
    },
    viewState: {
      type: Number
    },
    minutes: {
      type: Number
    },
    seconds: {
      type: Number
    },
    intervalId: {
      type: Number
    },
    isPlay: {
      type: Boolean
    },
    viewState: {
      type: Boolean
    }
  },
  methods: {
    handleViewState: function() {
      this.$emit("handleViewState", 0);
    },
    handleFold: function(e) {
      if (e.target.title === "TODO") {
        this.todoFoldState = !this.todoFoldState;
      } else {
        this.doneFoldState = !this.doneFoldState;
      }
    },
    handleTimer: function(isplay) {
      this.$emit("handleTimer", isplay);
    }
  },
  components: {
    AddNewMission,
    TaskListBox,
    ListHeader,
    Play
  }
};
</script>
<style lang="scss" scoped>
.todoListView {
  width: 100%;
  height: 100%;
  background-color: #003164;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  position: relative;
  .listColumn {
    width: 455px;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
  }
  .timerBox {
    position: absolute;
    left: 85px;
    bottom: 0px;
    .halfCircle {
      width: 350px;
      height: 175px;
      background-color: #ffedf7;
      border-top-left-radius: 350px;
      border-top-right-radius: 350px;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      .time {
        font-size: 64px;
        font-family: "roboto";
        font-weight: bold;
        color: #ff4384;
      }
      .playbtnBox {
        position: absolute;
        top: -60px;
        left: 115px;
        width: 120px;
        height: 120px;
        border-radius: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #003164;
      }
    }
  }
}
.hidden {
  visibility: hidden;
}
</style>

