<template>
  <div class="todoListView">
    <NavButton />
  </div>
</template>
<script>
import NavButton from "../components/todoListComponents/NavButton.vue";

export default {
  name: "todoList",
  components: {
    NavButton
  }
};
</script>
<style lang="scss" scope d>
.todoListView {
  width: 100%;
  height: 100%;
  background-color: #003164;
}
</style> 
