<template>
  <div>我是孙组件</div>
  <div>我是从父组件传过来的{{ value }}</div>
  <button @click="changeVal(10)">修改父组件传过来的值+10</button>
</template>

<script>
import { inject } from "vue";

export default {
  name: "GrandSon",
  setup() {
    const value = inject("value");
    const changeVal = inject("changeVal");
    return { value, changeVal };
  },
};
</script>
