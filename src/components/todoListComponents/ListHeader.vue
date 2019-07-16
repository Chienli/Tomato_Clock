<template>
  <div @click="handleFold" :class="{listHeader:true}" :title="title">
    <div :class="{updown:true , rotateArrow : foldState}">▲</div>
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
    },
    foldState: {
      type: Boolean
    }
  }
};
</script>
<style lang="scss" scoped>
.listHeader {
  width: 445px;
  height: 44px;
  margin-bottom: 16px;
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
