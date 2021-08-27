<template>
  <!-- 首页的推荐关注模块 -->
  <view class="firstNav">
    <view class="iconfont icon-sousuo icon"></view>
    <view class="middle">
      <navigator
        open-type="switchTab"
        url="/pages/index/index"
        class="text"
        :style="recommend"
        >推荐</navigator
      >
      <navigator
        open-type="navigate"
        url="/pages/follow/follow?tip=true"
        class="text"
        :style="follow"
        >关注</navigator
      >
    </view>
  </view>
</template>

<script>
export default {
  props: ["page"],
  data() {
    return {
      recommend: "",
      follow: "",
      color:"color: #ffffff;"
    };
  },
  mounted() {
    if (this.page === "recommend") {
      this.recommend = this.color;
    } else {
      this.follow = this.color;
    }
  },
};
</script>

<style>
.firstNav {
  width: 100%;
  position: fixed;
  top: 25px;
  left: 0;
  height: 35px;
  line-height: 35px;
  margin: 0 auto;
  z-index: 20;
}
.icon {
  position: absolute;
  top: 0;
  left: 0;
  color: #fff;
  width: 20%;
  text-align: center;
  font-size: 20px;
}
.middle {
  text-align: center;
  position: relative;
}
.text {
  display: inline;
  margin: 0 10px;
  color: #ffffffa9;
}
</style>