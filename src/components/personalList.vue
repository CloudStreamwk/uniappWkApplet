<template>
  <!-- 个人页面视频模块 -->
  <view>
    <view class="personalList">
      <view class="item">
        <video
          class="video"
          src="http://119.23.75.107/video/3-1.mp4"
          :controls="false"
          objectFit="cover"
        ></video>
        <view class="love-box">
          <text class="iconfont icon-aixin love-icon">12.3w</text>
        </view>
      </view>
    </view>
    <view class="more">没有更多了~</view>
    <view class="ground"></view>
  </view>

</template>

<script>
export default {};
</script>

<style>
.personalList {
  width: 100%;
  overflow: hidden;
  padding-left: 1%;
  background-color: #111218;
}
.item {
  width: 32%;
  height: 130px;
  float: left;
  position: relative;
  margin-right: 1%;
  margin-bottom: 1%;
}
.love-box {
  position: absolute;
  bottom: 5px;
  left: 8px;
}
.video {
  width: 100%;
  height: 100%;
}
.love-icon {
  font-size: 14px;
  color: #fff;
}
.more {
  width: 100%;
  height: 30px;
  line-height: 30px;
  text-align: center;
  font-size: 12px;
  color: #ffffffad;
  background-color: #111218;
}
.ground {
  width: 100%;
  height: 60px;
  background-color: #111218;
}
</style>