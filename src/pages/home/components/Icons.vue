<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page,index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.index">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.url" width="50px" height="50px">
          </div>
          <p class="icon-desc">{{item.title}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>
<script>
export default {
  name: "HomeIcons",
  data() {
    return {
      swiperOption: {
        // loop: true
      },
      iconList: [
        { url: "../../../static/img/4.png", index: "1", title: "热门景点热门景点" },
        { url: "../../../static/img/5.png", index: "2", title: "热门景点" },
        { url: "../../../static/img/6.png", index: "3", title: "热门景点" },
        { url: "../../../static/img/7.png", index: "4", title: "热门景点" },
        { url: "../../../static/img/8.png", index: "5", title: "热门景点" },
        { url: "../../../static/img/9.png", index: "6", title: "热门景点" },
        { url: "../../../static/img/10.png", index: "7", title: "热门景点" },
        { url: "../../../static/img/11.png", index: "8", title: "热门景点" },
        { url: "../../../static/img/4.png", index: "1", title: "热门景点" },
        { url: "../../../static/img/5.png", index: "2", title: "热门景点" }
      ]
    };
  },
  computed: {
      pages () {
          const pages=[]
          this.iconList.forEach((item,index)=>{
            const page=Math.floor(index/8)
            if(!pages[page]){
                pages[page]=[]
            }
            pages[page].push(item)
          })
          return pages
      }
  }
};
</script>
<style lang="stylus" scoped>
.icons >>> .swiper-container {
  height: 0;
  padding-bottom: 50%;
}
.icons{
  margin-top : .1rem;
}
.icon {
  position: relative;
  overflow: hidden;
  float: left;
  width: 25%;
  padding-bottom: 25%;
}

.icon-img {
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0.44rem;
  box-sizing: border-box;
  padding: 0.1rem;
}

.icon-img-content {
  margin: 0 auto;
  display: block;
}

.icon-desc {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0.22rem;
  height: 0.44rem;
  line-height: 0.44rem;
  color: #333;
  text-align: center;
  overflow: hidden;
  white-space :nowrap;
  text-overflow :ellipsis;
}
</style>

