<template>
  <div class="page-home">
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
    <Swiper :autoplay="2000" :loop="true" @change="changeHandler">
      <SwiperItem>1</SwiperItem>
      <SwiperItem>2</SwiperItem>
      <SwiperItem>3</SwiperItem>
    </Swiper>
  </div>
</template>

<script>
import { Swiper, SwiperItem } from "@/components/Swiper";
import { getBanner } from "@/api/cartoon";
export default {
  name: "Home",
  components: {
    Swiper,
    SwiperItem
  },
  methods: {
    changeHandler(payload) {
      console.log("index", payload);
    }
  },
  created() {
    /* // fetch('https://mhd.zhuishushenqi.com/comic_v2/getproad?apptype=8&appversion=1.0&channel=web-app&adgroupid=123')
    //   .then(res => res.json())
    //   .then(res => {
    //     console.log(res);
    //   })
    fetch('http://localhost:8080/migu/today/')
      .then(res => res.json())
      .then(res => {
        console.log(res);
      }) */

    //下载轮播图的数据
    getBanner().then(res => {
      console.log(res);
    });
  }
};
</script>
<style lang="scss" scoped>
@import "~@/assets/styles/mixins.scss";
.page-home {
  display: flex;
  flex-direction: column;
  height: 100%;
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
  }
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
