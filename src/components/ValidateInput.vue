<template>
  <div class="validate-input-container pb-3">
    <input
      type="email"
      class="form-control"
      id="exampleInputEmail1"
      v-model="inputRef.val"
      @blur="validateInput"
    />
    <div class="form-text" v-if="emailRef.error">
      {{ emailRef.message }}
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, PropType, reactive } from "vue";
const emailReg = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
interface RuleProp {
  type: "required" | "email"; // 可扩展
  message: String;
}
export type RulesProp = RuleProp[];
export default defineComponent({
  props: {
    rules: {
      type: Array as PropType<RulesProp>,
    },
  },
  setup(props) {
    const inputRef = reactive({
      val: "",
      error: false,
      message: "",
    });
    const validateInput = () => {
      if (props.rules) {
        const allPassed = props.rules.every((rule) => {});
      }
      if (inputRef.val.trim() === "") {
        inputRef.error = true;
        inputRef.message = "不可为空";
      } else if (!emailReg.test(inputRef.val)) {
        inputRef.error = true;
        inputRef.message = "邮箱不正确";
      }
    };
    return {
      inputRef,
      validateInput,
    };
  },
});
</script>

<style></style>
