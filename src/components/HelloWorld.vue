<script setup lang="ts">
import {
  ref,
  toRefs,
  toRef,
  useAttrs,
  useSlots,
  defineEmits,
  defineExpose,
  onMounted,
  getCurrentInstance,
} from "vue";

const instance: any = getCurrentInstance();
const _this = instance.appContext.config.globalProperties;
console.log(instance);
const props = defineProps({
  title: {
    type: String,
    required: false,
  },
  msg: String,
});
console.log("这是ref：", instance.refs);
const { title } = toRefs(props);
const count = ref(0);

const forDemo = () => {
  var i = 0;
  for (var i = 4; i < 9; i++) {
    console.log(i);
  }
};

const obj = {
  name: "gs",
  age: "18",
};

console.dir(obj);
console.log(obj);

onMounted(() => {
  console.log("mounted方法运行了");
  console.log("这是ref：", instance.refs);
  let pDom = document.getElementById("pDom");
  console.log(pDom);
  const fn1 = (event: any) => {
    console.log(obj.name);
    if (
      event &&
      event.target &&
      event.target.nodeName &&
      event.target.nodeName === "LI"
    ) {
      console.log("第一个kkk的this指向", this, event.target.nodeName);
    }
  };
  const fn2 = function (event: any) {
    console.log(obj.name);
    if (
      event &&
      event.target &&
      event.target.nodeName &&
      event.target.nodeName === "LI"
    ) {
      console.log("第二个kkk的this指向", this, event.target.nodeName);
    }
  };

  if (pDom) {
    console.log(pDom);
    console.log(this);
    // pDom.addEventListener("click", fn1, false);
    pDom.addEventListener("click", fn2, true);
  }
});
</script>

<template>
  <h1>{{ msg }}</h1>

  <p>
    Recommended IDE setup:
    <a href="https://code.visualstudio.com/" target="_blank">VS Code</a>
    +
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
  </p>

  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Documentation
    </a>
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Documentation</a>
  </p>

  <button type="button" @click="count++">count is: {{ count }}</button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
  <ul id="pDom">
    <li>{{ title }}</li>
    <li>{{ title }}</li>
    <li>{{ title }}</li>
    <li>{{ title }}</li>
    <li>{{ title }}</li>
    <li>{{ title }}</li>
    <li>{{ title }}</li>
    <li>{{ title }}</li>
    <li>{{ title }}</li>
    <li>{{ title }}</li>
  </ul>
  <p @click="forDemo" ref="ppp" v-show="false">{{ title }}</p>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
