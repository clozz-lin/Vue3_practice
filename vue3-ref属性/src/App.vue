<template>
  <div>
    <div>ref属性</div>
    <div>请打开控制台</div>
    <hr />
    <p>1. 获取单个元素</p>
    <div ref="dom">获取单个元素</div>
    <button @click="editOne">修改数据</button>
    <p>2. 被遍历的元素</p>
    <ul>
      <li v-for="i in 4" :key="i" :ref="setDom">第{{ i }}个li</li>
    </ul>
    <button @click="editTwo">
      通过ref获取多个元素并修改了第3个li的innerHTML
    </button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "App",
  setup() {
    // 1. 获取单个元素
    // 1.1 先定义一个空的响应式数据ref定义的
    // 1.2 setup中返回该数据，你想获取那个dom元素，在该元素上使用ref属性绑定该数据即可。
    const dom = ref(null);
    const editOne = () => {
      dom._value.innerHTML = "通过ref获取到了单个元素并修改了innerHTML";
      console.log(dom._value.innerHTML);
    };

    // 2. 获取v-for遍历的元素
    // 2.1 定义一个空数组，接收所有的LI
    // 2.2 定义一个函数，往空数组push DOM
    const domList = [];
    const setDom = (el) => {
      domList.push(el);
    };
    const editTwo = () => {
      domList[2].innerHTML = "我被修改了";
    };

    return { dom, editOne, setDom, domList, editTwo };
  },
};
</script>
