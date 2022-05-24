<template>
  <div>
    <div>watch函数</div>
    <div>请打开控制台</div>
    <hr />
    <p>1. 监听一个ref数据</p>
    <div id="refValue">这是一个ref数据:{{ refValue }}</div>
    <button @click="editRefValue">修改数据</button>
    <p>2. 监听一个reactive数据</p>
    <div id="reactiveVal">这是一个reactive数据:{{ reactiveVal.age }}</div>
    <button @click="editReactive">修改数据</button>
  </div>
</template>

<script>
import { ref, reactive, watch } from "vue";

export default {
  name: "App",
  setup() {
    // 1. 监听一个ref数据
    const refValue = ref(0);
    const editRefValue = () => {
      document.getElementById("refValue").innerHTML = "ref数据被修改了";
      return refValue.value++;
    };
    watch(refValue, (newVal, oldVal) => {
      console.log("监听到ref数据被修改了");
      // console.log(newVal, oldVal);
    });

    // 2. 监听一个reactive数据
    const reactiveVal = reactive({
      name: "ls",
      age: 10,
    });
    const editReactive = () => {
      document.getElementById("reactiveVal").innerHTML = "reactive数据被修改了";
      return reactiveVal.age++;
    };
    watch(reactiveVal, () => {
      console.log("监听到reactive数据被修改了");
    });

    return { refValue, editRefValue, reactiveVal, editReactive };
  },
};
</script>
