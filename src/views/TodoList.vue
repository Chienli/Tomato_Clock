<template>
  <div class="todoListView">
    <div class="circle">
      <div class="playbtnBox">
        <Play class="playbtn" :todoListView="true" />
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
  .listColumn {
    width: 455px;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
  }
  .circle {
    width: 350px;
    height: 350px;
    background-color: #ffedf7;
    border-radius: 100%;
    position: relative;
    .playbtnBox {
      position: absolute;
      width: 120px;
      height: 120px;
      border-radius: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      left: 0px;
      top:0px;
      background-color: #003164;
      .playbtn {
        
      }
    }
  }
}
.hidden {
  visibility: hidden;
}
</style>

