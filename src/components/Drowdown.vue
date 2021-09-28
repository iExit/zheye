<template>
  <div class="dropdown">
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
import { defineComponent, ref } from "vue";
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
    return {
      isOpen,
      toggleOpen,
    };
  },
});
</script>

<style></style>
