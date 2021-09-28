<template>
  <div class="container">
    <GlobalHeader :user="currentUser" />
    <ColumnList :list="list" />
  </div>
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import "bootstrap/dist/css/bootstrap.min.css";
import ColumnList, { ColumnProps } from "./components/ColumnList.vue";
import GlobalHeader, { UserProps } from "./components/GlobalHeader.vue";
const testData: ColumnProps[] = [
  {
    id: 1,
    title: "标题",
    description: "描述",
    avatar:
      "https://publish-pic-cpu.baidu.com/baab901d-7b89-476c-9bae-72cc2db93239.jpeg@w_228,h_152",
  },
  {
    id: 2,
    title: "标题",
    description: "描述",
    avatar: require("./assets/logo.png"),
  },
  {
    id: 3,
    title: "标题",
    description: "描述",
    avatar: null,
  },
  {
    id: 4,
    title: "标题",
    description: "描述",
    avatar: null,
  },
];
const currentUser: UserProps = {
  isLogin: true,
  name: "cici",
};
export default defineComponent({
  components: {
    ColumnList,
    GlobalHeader,
  },
  setup() {
    return {
      list: testData,
      currentUser,
    };
  },
});
</script>

<style lang="scss"></style>
