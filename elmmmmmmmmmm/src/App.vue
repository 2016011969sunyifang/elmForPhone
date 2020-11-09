<template>
  <div>
    <transition name="router-fade" mode="out-in">
      <!-- 有数据显示第一个没数据显示第二个 -->
      <keep-alive>
        <router-view v-if="$route.meta.keepAlive"></router-view>
      </keep-alive>
    </transition>
    <transition name="router-fade" mode="out-in">
      <router-view v-if="!$route.meta.keepAlive"></router-view>
    </transition>
    <svg-icon></svg-icon>
  </div>
</template>

<script>
// 懒加载
import svgIcon from "./components/common/svg";
export default {
  components: {
    svgIcon,
  },
};
</script>

<style lang="scss">
@import "./style/common";
.router-fade-enter-active,
.router-fade-leave-active {
  transition: opacity 0.3s;
}
.router-fade-enter,
.router-fade-leave-active {
  opacity: 0;
}
</style>
