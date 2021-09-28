<template>
  <div class="container">
    <GlobalHeader :user="currentUser" />
    <form>
      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">邮箱地址</label>
        <ValidateInput :rules="emailRules" />
        <div class="form-text" v-if="emailRef.error">
          {{ emailRef.message }}
        </div>
      </div>
      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">密码</label>
        <input
          type="password"
          class="form-control"
          id="exampleInputPassword1"
        />
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
    <!-- <ColumnList :list="list" /> -->
  </div>
  <router-view />
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";
import "bootstrap/dist/css/bootstrap.min.css";
import ColumnList, { ColumnProps } from "./components/ColumnList.vue";
import GlobalHeader, { UserProps } from "./components/GlobalHeader.vue";
import ValidateInput, { RulesProp } from "./components/ValidateInput.vue";
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
    ValidateInput,
  },
  setup() {
    const emailRules: RulesProp = [
      { type: "required", message: "不能为空" },
      { type: "email", message: "格式不正确" },
    ];
    return {
      list: testData,
      currentUser,
      emailRules,
    };
  },
});
</script>

<style lang="scss"></style>
