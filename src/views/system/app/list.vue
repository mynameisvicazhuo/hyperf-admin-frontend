<template>
  <div>
    <a-modal v-model:visible="isShow" :body-style="{'padding':'0px',height:'100%'}" :closable="false" :footer="false" fullscreen>
      <a-layout class="layout-main">
        <app-menu @set-app-page="setPage" :menus="menuItemList"></app-menu>
        <a-layout>
          <app-breadcrumb @closeWindonw="closeWindonw"></app-breadcrumb>
          <app-main ref="appMainComponent"></app-main>
        </a-layout>
      </a-layout>
    </a-modal>
  </div>
</template>

<script>
import appMenu from "./components/appMenu.vue";
import appMain from "./components/appMain.vue";
import appBreadcrumb from "./components/appBreadcrumb.vue";
import {ref} from "vue";

export default {
  name: "sys-app-list",
  components: {
    appMenu,
    appMain,
    appBreadcrumb,
  },
  setup() {
    const componentName = ref('');
    const isShow = ref(true);
    const appMainComponent = ref(null);

    const menuItemList = ref([{
      title: "订单管理",
      icon: "ma-icon-permission",
      page: "order/index",
      children: [
        {title: "房屋委托订单", icon: "", page: "HouseRentOutline"},
        {title: "看房订单", icon: "", page: "Component2"},
        {title: "看房订单", icon: "", page: "Component3"},
        {title: "入住签约订单", icon: "", page: "Component4"},
        {title: "电子锁报修", icon: "", page: "order/order5"},
        {title: "维修保洁订单", icon: "", page: "order/order6"}
      ]
    }, {
      title: "用户列表",
      icon: "ma-icon-permission",
      page: "user/index",
      children: [
        {title: "房屋委托订单", icon: "", page: "user/Arcoui"},
        {title: "看房订单", icon: "", page: "user/Arcoui"},
        {title: "看房订单", icon: "", page: "user/Arcoui"},
        {title: "入住签约订单", icon: "", page: "user/Arcoui"},
        {title: "电子锁报修", icon: "", page: "user/Arcoui"},
        {title: "维修保洁订单", icon: "", page: "user/Arcoui"}
      ]
    }, {
      title: "房源管理",
      icon: "ma-icon-permission",
      page: "demo5",
      children: []
    }])
    const setPage = (url) => {
      console.log(url)
      appMainComponent.value.loadComponents(url)
    }
    const closeWindonw = (value) => {
      isShow.value = value;
    }
    return {
      menuItemList,
      componentName,
      appMainComponent,
      isShow,
      closeWindonw,
      setPage
    };
  }

}
</script>

<style scoped>
img {
  width: 200px;
}

.h1 {
  border: 5px solid red !important;
  padding: 1px !important;
}

.section {
  border: 1px solid black;
  padding: 10px;
}
</style>