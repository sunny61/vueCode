<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item in iconList" :key="item.index">
        <div class="item-img-wrapper">
          <img class="item-img" :src="item.url">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "recommend",
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
          url: "../../../static/img/13.jpg",
          index: "2",
          title: "云南丽江山水欢迎您!",
          desc: "云南是一个多民族的省份，语言文字丰富多彩。"
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
  // margin-top : .1rem;
  line-height: 0.8rem;
  background: #eee;
  text-indent: 0.2rem;
}

.item {
  display: flex;
  height: 1.9rem;
  overflow: hidden;
}

.item-img {
  width: 1.7rem;
  height: 1.7rem;
  padding: 0.1rem;
}

.item-info {
  flex: 1;
  padding: 0.1rem;
  min-width: 0;
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

.item-button {
  line-height: 0.44rem;
  margin-top: 0.16rem;
  background: #ff9300;
  padding: 0 0.2rem;
  border-radius: 0.06rem;
  color: #fff;
}
</style>


