<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">北京</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item in hotCities" :key="item.id">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) in cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div
            class="item border-bottom"
            v-for="innerItem in item"
            :key="innerItem.id"
          >{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from "better-scroll";
export default {
  name: "cityList",
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.wrapper);
  },
  watch: {
    letter() {
      if (this.letter) {
        console.log(this.letter);
        const element = this.$refs[this.letter][0];
        console.log(element);
        this.scroll.scrollToElement(element);
      }
    }
  },
  components: {}
};
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.list {
  overflow: hidden;
  position: absolute;
  left: 0;
  right: 0;
  top: 1.58rem;
  bottom: 0;
}

.area {
}

.title {
  line-height: 0.54rem;
  background: #eee;
  color: #666;
  padding-left: 0.2rem;
  font-size: 0.26rem;
}

.button-list {
  overflow: hidden;
  padding: 0.1rem;
}

.button-wrapper {
  width: 33.33%;
  float: left;
}

.button {
  text-align: center;
  margin: 0.1rem;
  border: 0.02rem solid #ccc;
  padding: 0.1rem 0;
}

.item-list {
}

.item {
  line-height: 0.76rem;
  color: #666;
  padding-left: 0.2rem;
}
</style>
