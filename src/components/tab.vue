<template>
  <!-- 底部tabBar模块 -->
  <view class="tab">
    <navigator
      open-type="switchTab"
      class="tab-box"
      url="/pages/index/index"
      :style="index"
    >首页</navigator>
    <navigator
      open-type="switchTab"
      class="tab-box"
      url="/pages/city/city"
      :style="city"
    >城市</navigator>
    <view class="tab-box">
      <view class="iconfont icon-jiahao icon-box"></view>
    </view>
    <navigator
      open-type="switchTab"
      class="tab-box"
      url="/pages/news/news"
      :style="news"
    >消息</navigator>
    <navigator
      open-type="switchTab"
      class="tab-box"
      url="/pages/personal/personal"
      :style="personal"
    >我</navigator>
  </view>
</template>

<script>
export default {
  props: ["page"],
  data() {
    return {
      index: "",
      city: "",
      news: "",
      personal: "",
      color: "color: #ffffff;",
    };
  },
  mounted() {
    if (this.page === "recommend") {
      this.index = this.color;
    } else if(this.page === "city"){
      this.city = this.color;
    } else if(this.page === "news"){
      this.news = this.color;
    }else{
      this.personal = this.color;
    }
  },
};
</script>

<style>
/* 底部tabBar样式 */
.tab {
  height: 8%;
  width: 100%;
  position: fixed;
  bottom: 0;
  left: 0;
  display: flex;
  z-index: 20;
  background-color: #000;
}
.tab-box {
  width: 20%;
  color: #ffffffa9;
  text-align: center;
  height: 50px;
  line-height: 50px;
  font-size: 16px;
}
.icon-box {
  width: 60%;
  height: 26px;
  background: #fff;
  color: #000;
  margin: 12px 20%;
  line-height: 28px;
  border-radius: 5px;
  font-size: 16px;
}
</style>