<template>
  <div class="todoListView">
    <div class="listColumn">
      <AddNewMission :color="false" />
      <div>
        <ListHeader :title="'TO-DO'" @handleFold="handleFold" />
        <TaskListBox :viewState="viewState" :todos="todos" />
      </div>
      <div>
        <ListHeader :title="'DONE'" @handleFold="handleFold" />
        <TaskListBox :viewState="viewState" :todos="done" />
      </div>
    </div>
    <button @click="handleViewState">Change View</button>
  </div>
</template>
<script>
import AddNewMission from "../components/shared/AddNewMission.vue";
import TaskListBox from "../components/shared/TaskListBox.vue";
import ListHeader from "../components/todoListComponents/ListHeader.vue";

export default {
  name: "todoList",
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
      console.log(e.target.title);
    }
  },
  components: {
    AddNewMission,
    TaskListBox,
    ListHeader
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
}
</style>

