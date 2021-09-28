<template>
  <div class="row">
    <div class="col" v-for="item in list" :key="item.id">
      <div class="card">
        <img class="card-img-top" :src="item.avatar" :alt="item.title" />
        <div class="card-body">
          <h5 class="card-title">{{ item.title }}</h5>
          <p class="card-text">{{ item.description }}</p>
          <a href="#" class="btn btn-primary">进入专栏</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
export interface ColumnProps {
  id: number;
  title: string;
  avatar: string;
  description: string;
}

export default defineComponent({
  name: "ColumnList",
  props: {
    list: {
      type: Array as PropType<ColumnProps[]>,
      required: true,
    },
  },
  setup(props) {
    const columnList = computed(() => {
      return props.list.map((column) => {
        if (column.avatar) {
          column.avatar = require("@/assets/logo.png");
        }
        return column;
      });
    });
    return {
      columnList,
    };
  },
});
</script>

<style scoped lang="scss"></style>
