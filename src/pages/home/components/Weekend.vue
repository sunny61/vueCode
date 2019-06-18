<template>
  <div>
    <div class="recommend-title">周末去哪</div>
    <ul>
      <li class="item border-bottom" v-for="item in iconList" :key="item.index">
        <div class="item-img-wrapper">
          <img class="item-img" :src="item.url" width="414" height="140">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "weekend",
  data() {
    return {
      iconList: [
        {
          url: "../../../static/img/12.jpg",
          index: "1",
          title: "国家AAAAA级旅游景区,云南丽江山水欢迎您!",
          desc:
            "云南是一个多民族的省份，语言文字丰富多彩。国家历史文化名城：昆明、大理、丽江、建水、巍山、会泽"
        },
        {
          url: "../../../static/img/14.jpg",
          index: "3",
          title: "云南丽江山水欢迎您!",
          desc: "云南是一个多民族的省份，语言文字丰富多彩。"
        },
        {
          url: "../../../static/img/15.jpg",
          index: "4",
          title: "云南丽江山水欢迎您!",
          desc: "云南是一个多民族的省份，语言文字丰富多彩。"
        }
      ]
    };
  }
};
</script>
<style lang="stylus" scoped>
.recommend-title {
  line-height: 0.8rem;
  background: #eee;
  text-indent: 0.2rem;
}

.item-img-wrapper{
  overflow: hidden;
  height: 0;
  padding-bottom:33.9%
  
}

.item-img {
  width: 100%;
}

.item-info {
  padding: 0.1rem;
}

.item-title {
  line-height: 0.54rem;
  font-size: 0.32rem;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.item-desc {
  line-height: 0.4rem;
  color: #ccc;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
</style>


