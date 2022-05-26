<template>
  <div>我是父组件</div>
  <div>我是父组件的{{ value }}</div>
  <hr />
  <son></son>
</template>

<script>
import { ref, provide } from "vue";
import Son from "./Son.vue";
export default {
  name: "App",
  components: {
    Son,
  },
  // 父组件的数据传递给子组件
  setup() {
    const value = ref(10);
    provide("value", value);

    const changeVal = (newVal) => {
      value.value += newVal;
    };
    provide("changeVal", changeVal);
    return { value, changeVal };
  },
};
</script>
