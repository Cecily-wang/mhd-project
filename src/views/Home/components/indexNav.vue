<template>
  <nav class="index-nav">
    <router-link to="/classify">
      <div class="nav-item">
        <!-- <i class="iconfont icon-icon_addmessage"></i> -->
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-fenlei"></use>
        </svg>
        <p class="nav-text font-24">分类</p>
      </div>
    </router-link>
    <router-link to="/ranking">
      <div class="nav-item">
        <!-- <i class="iconfont icon-icon_addresslist"></i> -->
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-paihangbang-"></use>
        </svg>
        <p class="nav-text font-24">排行</p>
      </div>
    </router-link>
    <router-link to="/vip">
      <div class="nav-item">
        <!-- <i class="iconfont icon-icon_addressbook"></i> -->
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-VIP1"></use>
        </svg>
        <p class="nav-text font-24">VIP专区</p>
      </div>
    </router-link>
    <router-link to="/hello/history">
      <div class="nav-item">
        <!-- <i class="iconfont icon-icon_at"></i> -->
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-riqi"></use>
        </svg>
        <p class="nav-text font-24">历史</p>
      </div>
    </router-link>
  </nav>
</template>

<script>
export default {
  name: "indexNav"
};
</script>

<style lang="scss" scoped>
@import "~@/assets/styles/mixins.scss";
.index-nav {
  @include border-bottom;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  height: 100px;
  .nav-item {
    text-align: center;
    .iconfont {
      font-size: 52px;
      line-height: 1.2;
    }
    .nav-text {
      color: #8d8d8d;
      font-weight: 500;
      text-align: center;
      margin: 0.13333333rem 0 0;
    }
  }
}
</style>
