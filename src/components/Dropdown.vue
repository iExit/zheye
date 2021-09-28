<template>
  <div class="dropdown" ref="dropdownRef">
    <button
      class="btn btn-secondary dropdown-toggle"
      type="button"
      id="dropdownMenuButton1"
      data-bs-toggle="dropdown"
      aria-expanded="false"
      @click="toggleOpen"
    >
      {{ title }}
    </button>
    <ul
      v-if="isOpen"
      class="dropdown-menu"
      :style="{ display: 'block' }"
      aria-labelledby="dropdownMenuButton1"
    >
      <slot />
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, watch } from "vue";
import useClickOutside from "../hooks/useClickOutside";
export default defineComponent({
  name: "Drowdown",
  props: {
    title: {
      type: String,
      required: true,
    },
  },
  setup() {
    const isOpen = ref(false);
    const toggleOpen = () => {
      isOpen.value = !isOpen.value;
    };
    const dropdownRef = ref<null | HTMLElement>(null);
    const isClickOutside = useClickOutside(dropdownRef);
    watch(isClickOutside, () => {
      if (isOpen.value && isClickOutside.value) {
        isOpen.value = false;
      }
    });
    return {
      isOpen,
      toggleOpen,
      dropdownRef,
    };
  },
});
</script>

<style></style>
