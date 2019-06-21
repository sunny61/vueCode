<template>
  <div>
    <div class="search">
      <input v-model="keyWord" class="search-input" type="text" placeholder="请输入城市名称或拼音">
    </div>
    <div class="search-content" ref="search" v-show="keyWord">
      <ul>
        <li
          class="search-item border-bottom"
          v-for="item in list"
          :key="item.id"
          @click="handleCityClick(item.name)"
        >{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配项</li>
      </ul>
    </div>
  </div>
</template>
<script>
import { clearTimeout, setTimeout } from "timers";
import BScroll from "better-scroll";
import { mapMutations } from "vuex";
export default {
  name: "CitySearch",
  props: {
    cities: Object
  },
  data() {
    return {
      keyWord: "",
      list: [],
      timer: null
    };
  },
  computed: {
    hasNoData() {
      return !this.list.length;
    }
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.search);
  },
  methods: {
    ...mapMutations(["changeCity"]),
    handleCityClick(city) {
      // 1、this.$store.dispatch("changeCity", city);提交数据至actions，由actions再提交到mutations
      // 2、this.$store.commit("changeCity", city);直接数据至mutations
      //3、 ...mapMutations(["changeCity"]),调用changeCity
      this.changeCity(city);
      this.$router.push("/");
    }
  },
  watch: {
    keyWord() {
      if (this.timer) {
        clearTimeout(this.timer);
      }
      if (!this.keyWord) {
        this.list = [];
        return;
      }
      this.timer = setTimeout(() => {
        const result = [];
        for (let i in this.cities) {
          this.cities[i].forEach(value => {
            if (
              value.spell.indexOf(this.keyWord) > -1 ||
              value.name.indexOf(this.keyWord) > -1
            ) {
              result.push(value);
            }
            this.list = result;
          });
        }
      }, 100);
    }
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.search {
  background: $bgColor;
  height: 0.72rem;
  padding: 0 0.1rem;
}

.search-input {
  width: 100%;
  box-sizing: border-box;
  padding: 0 0.1rem;
  height: 0.62rem;
  line-height: 0.62rem;
  text-align: center;
  border-radius: 0.06rem;
}

.search-content {
  z-index: 1;
  overflow: hidden;
  position: absolute;
  top: 1.58rem;
  left: 0;
  right: 0;
  bottom: 0;
  background: #eee;
}

.search-item {
  line-height: 0.62rem;
  padding-left: 0.2rem;
  color: #666;
  background: #fff;
}
</style>

