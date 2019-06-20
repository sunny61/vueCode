<template>
  <div class="header">
    城市选择
    <router-link to="/">
    <div class="iconfont header-back">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: "cityHeader",
  components: {}
};
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.header {
  position: relative;
  overflow: hidden;
  height: 0.86rem;
  line-height: 0.86rem;
  text-align: center;
  color: #fff;
  background: $bgColor;
}

.header-back {
  font-size: 0.4rem;
  width: 0.64rem;
  text-align: center;
  position: absolute;
  top: 0;
  color: #fff;
}
</style>
