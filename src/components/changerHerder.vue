<template>
  <!-- 切换城市头部搜索模块 -->
  <view>
    <view class="changeHeader">
      <navigator
        open-type="navigateBack"
        delta="1"
        animation-type="side-out-bottom"
        animation-duration="300"
        class="change"
      >
        <view class="iconfont icon-cuowu left"></view>
        <view class="title"> 切换城市 </view>
      </navigator>
      <view class="citySousuo">
        <view class="iconfont icon-sousuo left"></view>
        <input class="sousuoContent" placeholder="输入城市或区县名搜索"></input>
      </view>
    </view>
    <view class="ground"> </view>
  </view>
</template>

<script>
export default {};
</script>

<style>
.changeHeader {
  width: 90%;
  padding: 0 5%;
  position: fixed;
  top: 0;
  left: 0;
  color: #ccc;
  background-color: #252525;
}
.ground {
  width: 100%;
  height: 96px;
}
/* 标题样式 */
.change {
  width: 100%;
  position: relative;
  height: 56px;
  margin: 0 auto;
  line-height: 80px;
}
.change .left {
  position: absolute;
  top: 2px;
  font-size: 15px;
}
.title {
  font-size: 16px;
  text-align: center;
  color: #fff;
}
/* 搜索城市 */
.citySousuo {
  width: 100%;
  margin: 2% 0;
  height: 26px;
  position: relative;

  background-color: #424242;
}
.citySousuo .left {
  position: absolute;
  left: 8px;
  font-size: 14px;
  height: 26px;
  line-height: 26px;
}
.sousuoContent {
  position: absolute;
  left: 28px;
  height: 26px;
  font-size: 12px;
  line-height: 26px;
}
</style>