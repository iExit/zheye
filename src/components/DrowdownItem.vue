<template>
  <li class="dropdown-option" :class="{ 'is-disabled': disabled }">
    <slot />
  </li>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
export default defineComponent({
  name: "DrowdownItemvue",
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  setup() {
    const isOpen = ref(false);
    const toggleOpen = () => {
      isOpen.value = !isOpen.value;
    };
    return {
      isOpen,
      toggleOpen,
    };
  },
});
</script>

<style lang="scss" scoped>
.dropdown-option {
  .is-disabled > * {
    color: #6c757d;
    pointer-events: none;
    background-color: transparent;
  }
}
</style>
