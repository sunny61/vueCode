<template>
  <div>
    <detail-banner :bannerImg="bannerImg" :sightName="sightName" :gallaryImgs="gallaryImgs"></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="list"></detail-list>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import DetailBanner from "./components/Banner";
import DetailHeader from "./components/Header";
import DetailList from "./components/List";
export default {
  name: "Detail",
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data() {
    return {
      list: [],
      bannerImg: "",
      sightName: "",
      gallaryImgs: []
    };
  },
  methods: {
    getDetailInfo() {
      axios
        .get("../static/mock/detail.json", {
          params: {
            id: this.$route.params.id
          }
        })
        .then(this.handleGetDetailInfoSucc);
    },
    handleGetDetailInfoSucc(res) {
      console.log(res.data);
      res = res.data;
      this.list = res.data.categoryList;
      this.bannerImg = res.data.bannerImg;
      this.sightName = res.data.sightName;
      this.gallaryImgs = res.data.gallaryImgs;
    }
  },
  //添加 <keep-alive>之后，mounted不执行，只有activated执行,本页面不需要缓存，因为根据用户点击的不同详情需要去请求数据
  //清除缓存的两种方式：
  // 1、执行
  //  activated() {
  //     this.getDetailInfo();
  //   }
  //2、App.vue 设置   <keep-alive exclude="Detail">
  //exclude="Detail"  为该页面的name
  mounted() {
    this.getDetailInfo();
  }
};
</script>
<style lang="stylus" scoped>
.content {
  height: 50rem;
}
</style>
