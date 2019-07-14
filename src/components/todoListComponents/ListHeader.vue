<template>
  <div @click="handleFold" class="listHeader" :title="title">
    <div class="updown">▲</div>
    {{title}}
  </div>
</template>
<script>
export default {
  name: "listHeader",
  methods: {
    handleFold: function(e) {
      this.$emit("handleFold", e);
    }
  },
  props: {
    title: {
      type: String
    }
  }
};
</script>
<style lang="scss" scoped>
.listHeader {
  width: 445px;
  height: 44px;
  background-color: #335a83;
  line-height: 44px;
  color: white;
  font-size: 24px;
  font-family: "roboto";
  font-weight: bold;
  box-sizing: border-box;
  padding: 0 20px;
  cursor: pointer;
  position: relative;
  .updown {
    font-size: 12px;
    position: absolute;
    right: 20px;
    top: 0px;
  }
  .rotateArrow {
    transform: rotate(180deg);
  }
}
</style>
