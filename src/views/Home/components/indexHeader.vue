<template>
  <header class="index-header">
    <a href="mine.html?cpid=0">
      <div class="header-user">
        <div class="user-btn"></div>
      </div>
    </a>
    <div class="header-logo"></div>
    <a href="search.html?cpid=0">
      <div class="header-search"></div>
    </a>
  </header>
</template>

<script>
export default {
  name: "indexHeader"
};
</script>

<style lang="scss" scoped>
@import "~@/assets/styles/mixins.scss";
.index-header {
  // border-bottom: 1px solid #ededed;
  // &::after {
  //   content: "";
  //   position: absolute;
  //   width: 100%;
  //   height: 1px;
  //   left: 0px;
  //   bottom: 0px;
  //   background-color: #ededed;
  //   transform: scaleY(0.5);
  // }
  // position: relative;
  @include border-bottom;
  display: flex;
  height: 44px;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  box-sizing: border-box;
  .header-user {
    width: 25px;
    height: 25px;
    background: url(~@/assets/icon/user-btn.png);
    background-size: 100%;
  }
  .header-logo {
    width: 92px;
    height: 28px;
    background: url(~@/assets/logo.png);
    background-size: 100%;
  }
  .header-search {
    width: 25px;
    height: 25px;
    background: url(~@/assets/icon/search.png);
    background-size: 100%;
  }
}
</style>
