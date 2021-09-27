<template>
  <div class="container">
    <ColumnList :list="list" />
  </div>
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import "bootstrap/dist/css/bootstrap.min.css";
import ColumnList, { ColumnProps } from "./components/ColumnList.vue";
const testData: ColumnProps[] = [
  {
    id: 1,
    title: "标题",
    description: "描述",
    avatar: require("./assets/logo.png"),
  },
  {
    id: 2,
    title: "标题",
    description: "描述",
    avatar: require("./assets/logo.png"),
  },
];
export default defineComponent({
  components: {
    ColumnList,
  },
  setup() {
    return {
      list: testData,
    };
  },
});
</script>

<style lang="scss"></style>
