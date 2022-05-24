<template>
  <div>
    <div>computed练习</div>
    <hr />
    <div>今年{{ age }}岁</div>
    <div>后年{{ newAge }}岁</div>
  </div>
</template>

<script>
import { ref, computed } from "vue";

export default {
  name: "App",
  setup() {
    const age = ref(16);
    const newAge = computed(() => {
      return age.value + 2;
    });
    return { age, newAge };
  },
};
</script>
