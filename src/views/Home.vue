<template>
  <div class="home"></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import HelloWorld from "@/components/ColumnList.vue"; // @ is an alias to /src

export default defineComponent({
  name: "Home",
  components: {
    HelloWorld,
  },
});
</script>
