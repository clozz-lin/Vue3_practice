<template>
  <div>我是父组件</div>
  <div>我是从父组件的{{ value }}</div>
  <hr />
  <son :value="value" @update:value="edit"></son>
  <son v-model:value="value"></son>
</template>

<script>
import { ref } from "vue";
import Son from "./Son.vue";
export default {
  name: "App",
  components: {
    Son,
  },
  // 父组件的数据传递给子组件
  setup() {
    const value = ref(10);

    const edit = (newVal) => {
      value.value = newVal;
    };
    return { value, edit };
  },
};
</script>
