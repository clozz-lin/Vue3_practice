<template>
  <div>我是子组件</div>
  <div>我是从父组件传过来的{{ value }}</div>
  <button @click="edit">修改父组件传过来的值</button>
</template>

<script>
import {} from "vue";

export default {
  name: "Son",
  props: {
    value: {
      type: Number,
      default: 0,
    },
  },
  setup(props, { emit }) {
    console.log(props.value);
    const edit = () => {
      emit("update:value", 20);
    };
    return { edit };
  },
};
</script>
