<template>
  <div class="page-home">
    <index-header></index-header>
    <div class="index-main">
      <!-- :loop="true"
        @change="changeHandler" -->
      <Swiper class="my-swiper" v-if="bannerList.length > 0" :autoplay="2000">
        <swiper-item v-for="item in bannerList" :key="item.id">
          <img :src="item.imageurl" alt />
        </swiper-item>
      </Swiper>
      <index-nav></index-nav>
      <index-recommend
        v-for="item in recommendList"
        :key="item.specialid"
        :info="item"
      ></index-recommend>
      <div class="my-icp">
        <a
          class="record"
          href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=31011202006214"
          target="_blank"
        >
          <img
            class="img"
            src="https://wechatapp.zhuishushenqi.com/mhd/201711/gongan.jpg"
          />
          <div>沪公网安备 31011202006214号</div>
        </a>
        <div class="licence">
          增值电信业务经营许可证沪B2-20170022
          <br />网络文化经营许可证沪网文（2016）3206-227号
          <br />出版物经营许可证新出发沪批字第U7659号
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Swiper, SwiperItem } from "@/components/Swiper";
import { getBanner, getIndexRecommend } from "@/api/cartoon";
import indexHeader from "./components/indexHeader";
import indexNav from "./components/indexNav";
import indexRecommend from "./components/indexRecommend";
export default {
  name: "Home",
  data() {
    return {
      bannerList: [],
      recommendList: []
    };
  },
  components: {
    Swiper,
    SwiperItem,
    indexHeader,
    indexNav,
    indexRecommend
  },
  methods: {
    changeHandler(payload) {
      console.log("index", payload);
    },
    getBanner() {
      //下载轮播图的数据
      getBanner()
        .then(res => {
          // console.log(res);
          if (res.code === 200) {
            this.bannerList = res.info;
          } else {
            alert(res.code_msg);
          }
        })
        .catch(err => {
          alert("网络异常，请稍后" + err);
        });
    },
    getIndexRecommend() {
      getIndexRecommend()
        .then(res => {
          if (res.code === 200) {
            this.recommendList = res.info;
          } else {
            // 不ok，就在页面上报错
            // 在这里我们先通过 alert 进行报错，后期 我们可以用一下 vant 组件库的组件
            alert(res.code_msg);
          }
        })
        .catch(err => {
          alert("网络异常，请稍后：" + err);
        });
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
    this.getBanner();
    this.getIndexRecommend();
  }
};
</script>
<style lang="scss" scoped>
@import "~@/assets/styles/mixins.scss";
.page-home {
  .index-main {
    flex: 1;
    overflow-y: auto;
  }
  .my-swiper {
    img {
      width: 100%;
    }
  }
  display: flex;
  flex-direction: column;
  height: 100%;
  .my-icp {
    padding: 5px 0;
    font-size: 12px;
    .record {
      display: flex;
      align-items: center;
      justify-content: center;
      .img {
        width: 15px;
        height: 15px;
        margin-right: 4px;
      }
    }
    .licence {
      margin-top: 4px;
      text-align: center;
    }
  }
}
</style>
<style>
.icon {
  width: 50px;
  height: 50px;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
</style>
