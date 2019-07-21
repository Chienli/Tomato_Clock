<template>
  <div class="tabListBox">
    <div :key="index" v-for="(tab,index) in TAB_LIST" class="tabList">
      <i :class="['fas', getIcon(tab.icon)]"></i>
      <div class="tabList-title">{{tab.title}}</div>
    </div>
  </div>
</template>
<script>
import { TAB_LIST } from "../../constant.js";
export default {
  name: "tabList",
  data() {
    return {
      TAB_LIST
    };
  },
  methods: {
    getIcon(icon) {
      switch (icon) {
        case "menu":
          return "fa-bars";
        case "chart":
          return "fa-chart-area";
        case "music":
          return "fa-music";
      }
    }
  }
};
</script>
<style lang="scss" scoped>
@mixin text-base {
  color: #ff4384;
  font-weight: bold;
  font-size: 32px;
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
    i {
      @include text-base;
    }
    .tabList-title {
      font-family: "roboto";
      width: 192px;
      letter-spacing: 1px;
      word-wrap: none;
      @include text-base;
    }
  }
}
</style>
