<template>
  <div class="swriper">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="item in list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" style="width:414px;height:175px;">
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>
<script>
export default {
  name: "HomeSwiper",
  props: {
    list: Array
  },
  data() {
    return {
      swiperOption: {
        speed: 2000,
        autoplay: {
          delay: 5000, //秒
          disableOnInteraction: false //滑动不会失效
        },
        pagination: ".swiper-pagination",
        loop: true
      }
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