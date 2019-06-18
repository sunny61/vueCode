<template>
  <div class="swriper">
    <swiper :options="swiperOption" v-if="loop.length>1">
      <!-- slides -->
      <swiper-slide v-for="(item, index) in loop" :key="index">
        <img class="swiper-img" :src="item.BUrl" style="width:414px;height:175px;">
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>
<script>
export default {
  name: "HomeSwiper",
  data() {
    return {
      swiperOption: {
        speed:2000,
        autoplay: {
          delay: 5000, //秒
          disableOnInteraction: false //滑动不会失效
        },
        pagination: ".swiper-pagination",
        loop: true
      },
      loop: [
        { BUrl: "../../../static/img/1.jpg", index: 1 },
        { BUrl: "../../../static/img/2.jpg", index: 2 },
        { BUrl: "../../../static/img/3.jpg", index: 3 }
      ]
    };
  }
};
</script>
<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active {
  background: #fff;
}
.swriper {
  overflow: hidden;
  width: 100%;
  height: 0;
  padding-bottom: 42.4%;
  background: #ccc;
}

.swiper-img {
  width: 100%;
}
</style>