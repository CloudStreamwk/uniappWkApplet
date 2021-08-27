<template>
<!-- 首页的左边视频相关信息模块 -->
  <view class="listLeft">
    <view class="author" > {{item.author}}</view>
    <view class="title"> {{item.title}}</view>
    <view class="musicBox">
        <view class="iconfont icon-yinle icon"></view>
        <view class="mbox">
            <view class="music">姜云升-你一定能够成为你想要去成为的人</view>
        </view>
        
    </view>
  </view>
</template>

<script>
export default {
  props: ["item"],
};
</script>

<style>
.listLeft {
  height: 110px;
  margin-left: 6px;
  color: #fff;
  width: 150px;
}
/* 作者 */
.author {
  height: 30px;
  line-height: 30px;
  font-size: 14px;
}
/* 标题 */
.title {
    height: 50px;
  line-height: 20px; 
  font-size: 12px;
  width: 100%;
  word-wrap: break-word;
}
.mbox{
    margin-left: 20px;
    width: 150px;
    overflow: hidden;
}
/* 背景音乐文字动画 */
.icon{
    position: absolute;
    height: 35px;
  line-height: 35px;
}
.music {
  height: 35px;
  line-height: 35px;
  font-size: 12px;
  width: 250px;
  word-wrap:normal;
  animation: 10s music linear 0.2s infinite;
}

@keyframes music{
    0%{
        transform: translate3d(80%,0,0);
    }
    100%{
        transform: translate3d(-80%,0,0);
    }
}
</style>