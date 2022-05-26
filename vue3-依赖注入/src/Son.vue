<template>
  <div>我是子组件</div>
  <div>我是从父组件传过来的{{ value }}</div>
  <button @click="changeVal(5)">修改父组件传过来的值+5</button>
  <hr />
  <grand-son></grand-son>
</template>

<script>
import GrandSon from "./GrandSon.vue";
import { inject } from "vue";

export default {
  name: "Son",
  components: {
    GrandSon,
  },
  setup() {
    const value = inject("value");
    const changeVal = inject("changeVal");
    return { value, changeVal };
  },
};
</script>
