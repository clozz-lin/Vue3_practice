<template>
  <div>
    <div>鼠标坐标</div>
    <div>x: {{ x }}</div>
    <div>y: {{ y }}</div>
  </div>
  <hr />
  <div>{{ count }} <button @click="add">累加1</button></div>
</template>

<script>
import { reactive, toRefs, onMounted, onUnmounted, ref } from "vue";

const useMouse = () => {
  // 记录鼠标坐标
  const mouse = reactive({
    x: 0,
    y: 0,
  });

  const move = (e) => {
    mouse.x = e.pageX;
    mouse.y = e.pageY;
  };

  onMounted(() => {
    document.addEventListener("mousemove", move);
  });
  onUnmounted(() => {
    document.removeEventListener("mousemove", move);
  });
  return mouse;
};

export default {
  name: "App",
  setup() {
    // 记录鼠标坐标
    const mouse = useMouse();

    // 数字累加
    const count = ref(0);
    const add = () => {
      count.value++;
    };
    return { ...toRefs(mouse), count, add };
  },
};
</script>
