<template>
  <div class="container">
    <GlobalHeader :user="currentUser" />
    <!-- <ValidateForm @form-submit="onFormSubmit">
      <div class="mb-3">
        <label class="form-label">邮箱地址</label>
        <ValidateInput
          type="text"
          placeholder="请输入邮箱地址"
          :rules="emailRules"
          v-model="emailValue"
        />
      </div>
      <div class="mb-3">
        <label class="form-label">密码</label>
        <ValidateInput
          type="password"
          placeholder="请输入密码"
          :rules="passwordRules"
          v-model="passwordValue"
        />
      </div>
      <template #submit>
        <span class="btn btn-danger">提交</span>
      </template>
    </ValidateForm> -->
    <router-view />
    <!-- <ColumnList :list="list" /> -->
    <GlobalFooter />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from "vue";
import "bootstrap/dist/css/bootstrap.min.css";
import GlobalHeader, { UserProps } from "./components/GlobalHeader.vue";
import GlobalFooter from "./components/GlobalFooter.vue";
import ValidateInput, { RulesProp } from "./components/ValidateInput.vue";
import ValidateForm from "./components/ValidateForm.vue";

const currentUser: UserProps = {
  isLogin: true,
  name: "cici",
};
export default defineComponent({
  components: {
    GlobalHeader,
    GlobalFooter,
  },
  setup() {
    const emailValue = ref("");
    const emailRules: RulesProp = [
      { type: "required", message: "不能为空" },
      { type: "email", message: "格式不正确" },
    ];
    const passwordValue = ref("");
    const passwordRules: RulesProp = [
      { type: "required", message: "不能为空" },
    ];
    const onFormSubmit = (result: any) => {
      console.log(result);
    };
    return {
      currentUser,
      emailValue,
      emailRules,
      passwordValue,
      passwordRules,
      onFormSubmit,
    };
  },
});
</script>

<style lang="scss"></style>
