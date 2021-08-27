<template>
  <!-- 消息头部 -->
  <view>
    <view class="newsNav">
      <view class="title"> 消息 </view>
    </view>
    <view class="ground"> </view>
  </view>

</template>

<script>
export default {};
</script>

<style>
.newsNav {
  position: fixed;
  width: 100%;
  height: 60px;
  border-bottom: 1px solid #5a5a5a69;
  z-index: 20;
  background-color: #181a22;
}
.ground {
  width: 100%;
  height: 60px;
}
.title {
  width: 100%;
  text-align: center;
  height: 56px;
  line-height: 80px;
  font-size: 15px;
  color: #fff;
}
</style>