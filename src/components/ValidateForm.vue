<template>
  <form class="validate-form-container">
    <slot name="default" />
    <div class="submit-area" @click.prevent="submitForm">
      <slot name="submit">
        <button type="submit" class="btn btn-primary">提交</button>
      </slot>
    </div>
  </form>
</template>

<script lang="ts">
import { defineComponent, onUnmounted } from "vue";
type ValidateFunc = () => boolean;
import mitt from "mitt";
export const emitter = mitt();
export default defineComponent({
  name: "ValidateForm",
  props: {},
  emits: ["form-submit"],
  setup(props, { emit }) {
    let funcArr: ValidateFunc[] = [];
    const submitForm = () => {
      // 遍历每个子组件的校验函数
      const result = funcArr.map((func) => func()).every((result) => result);
      emit("form-submit", result);
    };
    const callback = (func?: ValidateFunc) => {
      funcArr.push(func!);
    };
    emitter.on("form-item-created", callback);
    onUnmounted(() => {
      emitter.off("form-item-created", callback);
      funcArr = [];
    });
    return {
      submitForm,
    };
  },
});
</script>

<style></style>
