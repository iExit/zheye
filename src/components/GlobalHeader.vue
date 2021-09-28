<template>
  <nav class="navbar navbar-dark bg-dark">
    <a class="navbar-brand" href="#">者也专栏</a>
    <ul v-if="!user.isLogin">
      <li>登录</li>
      <li>注册</li>
    </ul>
    <ul v-else>
      <li>
        <Drowdown :title="`你好${user.name}`">
          <DrowdownItem>
            <a href="#" class="dropdown-item">新建文章</a></DrowdownItem
          >
          <DrowdownItem disabled>
            <a href="#" class="dropdown-item">编辑资料</a></DrowdownItem
          >
          <DrowdownItem>
            <a href="#" class="dropdown-item">退出登录</a></DrowdownItem
          >
        </Drowdown>
      </li>
    </ul>
  </nav>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Drowdown from "./Dropdown.vue";
import DrowdownItem from "./DropdownItem.vue";
export interface UserProps {
  isLogin: boolean;
  name?: string;
  id?: number;
}

export default defineComponent({
  name: "GlobalHeader",
  components: { Drowdown, DrowdownItem },
  props: {
    user: {
      type: Object as PropType<UserProps>,
      required: true,
    },
  },
  setup() {},
});
</script>

<style></style>
