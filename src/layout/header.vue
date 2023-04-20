<script lang="ts">
import { ref, reactive } from "vue";

interface RouterObject {
  routerLink: string;
  routerTitle: string;
}

export default {
  name: "TheHeader",

  setup() {
    const title = ref("电子印章公共服务平台");
    const routerObj = reactive([
      {
        routerLink: "/",
        routerTitle: "首页",
      },
      {
        routerLink: "/seal",
        routerTitle: "印章服务",
      },
      {
        routerLink: "/temManage",
        routerTitle: "模版管理",
      },
      {
        routerLink: "/statiForm",
        routerTitle: "统计报表",
      },
      {
        routerLink: "/userCenter",
        routerTitle: "用户中心",
      },
    ]);
    return {
      title: title,
      routerObj: routerObj,
    };
  },
};
</script>

<template>
  <div class="header">
    <div class="containerLeft">
      <p>{{ title }}</p>
    </div>
    <div class="containerRight">
      <div
        class="containerItem"
        v-for="(item, index) in routerObj"
        :key="index"
      >
        <routerLink class="children" :to="item.routerLink">{{
          item.routerTitle
        }}</routerLink>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.header {
  width: 1440px;
  height: 64px;
  background: linear-gradient(90deg, #2365cf 0%, #3e95e7 100%);
  display: flex;
}

.containerLeft {
  flex: 0 0 240px;

  p {
    font-family: PingFangSC-Regular;
    font-size: 18px;
    color: #ffffff;
    font-weight: 400;
    line-height: 64px;
    text-align: center;
  }
}

.containerRight {
  flex: 1 1 100%;
  display: flex;
  padding-left: 31px;

  .containerItem {
    margin-left: 45px;

    .children {
      font-family: PingFangSC-Regular;
      font-size: 16px;
      color: #ffffff;
      font-weight: 400;
      line-height: 64px;
    }
  }

  :first-child {
    padding-left: 0px;
  }
}
</style>
