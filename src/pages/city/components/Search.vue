<template>
  <div class="search">
    <input class="search-input" type="text" placeholder="请输入城市名称或拼音">
  </div>
</template>
<script>
export default {
  name: "CitySearch"
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
</style>

