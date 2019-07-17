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
    <div class="tabListBox">
      <div :key="index" v-for="(tab,index) in tabList" class="tabList">
        <div :class="[tab.icon]"></div>
        <div>{{tab.title}}</div>
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
    <div class="navbar">
      <div @click="handleViewState" class="cross">✖</div>
      <div class="pomodoro">POMODORO</div>
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
      doneFoldState: false,
      tabList: [
        {
          icon: "menu",
          title: "TO-DO LIST"
        },
        {
          icon: "chart",
          title: "ANALYTICS"
        },
        {
          icon: "music",
          title: "RINGTONES"
        }
      ]
    };
  },
  props: {
    todos: {
      type: Array
    },
    done: {
      type: Array
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
  justify-content: space-around;
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
  .navbar {
    width: 36px;
    height: 700px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    .cross {
      color: white;
      font-size: 30px;
      font-weight: bold;
      font-family: "roboto";
      display: flex;
      flex-direction: column;
      align-items: center;
      cursor: pointer;
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
  .tabListBox {
    height: 700px;
    .tabList {
      width: 236px;
      height: 42px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin: 42px 0;
      cursor: pointer;
      img {
        width: 36px;
        height: 36px;
      }
      div:nth-child(1) {
        width: 32px;
        height: 32px;
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        &.menu {
          background-image: url(../../public/menu_pink.png);
        }
        &.chart {
          background-image: url(../../public/chart_pink.png);
        }
        &.music {
          background-image: url(../../public/music_pink.png);
        }
      }
      div:nth-child(2) {
        width: 192px;
        color: #ff4384;
        font-family: bold;
        font-size: 36px;
        text-align: left;
        font-family: "roboto";
        font-weight: bold;
      }
    }
  }
}
.hidden {
  visibility: hidden;
}
</style>

