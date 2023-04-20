<template>
  <div>layout {{ title }}</div>
</template>

<script lang="ts">
import { ref } from "vue";
export default {
  setup() {
    const title = ref("首页");
    console.log(title);
    return {
      title,
    };
  },
};
</script>

<style></style>
