<template>
  <!-- 消息内容模块 -->
  <view class="newsContent">
    <view class="citySousuo">
      <view class="iconfont icon-sousuo left"></view>
      <input
        class="sousuoContent"
        placeholder="搜索"
      ></input>
    </view>
    <view class="newsList">
      <view
        class="item"
        v-for="(item,index) of list"
        :key="item.id"
      >
        <view class="author-img-box">
          <image
            class="author-img"
            :src="'http://119.23.75.107/img/message/'+item.src"
          ></image>
        </view>
        <view class="text">
          <view class="top">
            <view class="name">{{item.name}}</view>
            <view class="tip">{{item.time}}</view>
          </view>
          <view class="content">
            {{item.content}}
          </view>
          <view class="iconfont icon-arrow-right right"></view>
        </view>
      </view>
      <view class="more">
        暂时没有更多了
      </view>
    </view>
  </view>
</template>

<script>
export default {
  props: ["list"],
};
</script>

<style>
.newsContent {
  height: 100%;
  width: 100%;
  color: #fff;
  z-index: 19;
  background-color: #111218ee;
  padding-top: 5%;
}
/* 搜索框 */
.citySousuo {
  width: 92%;
  margin: 0 4% 3% 4%;
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
  color: #ccccccb6;
}
.sousuoContent {
  position: absolute;
  left: 28px;
  height: 26px;
  font-size: 12px;
  line-height: 26px;
}
/* 消息列表 */
.newsList {
  width: 100%;
  height: 100%;
  position: relative;
}
.item {
  width: 100%;
  display: inline-block;
}
.author-img-box {
  float: left;
  width: 15%;
  padding: 2% 0 3% 5%;
}
.author-img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
/* 信息提示 */
.text {
  position: relative;
  width: 80%;
  float: left;
  letter-spacing: 0.5px;
  padding: 4% 0;
  border-bottom: 1px solid #5a5a5a69;
}
.top {
  font-size: 12px;
  height: 12px;
  line-height: 12px;
}
.name {
  display: inline-block;
  font-size: 13.2px;
}
.tip {
  display: inline;
  font-size: 8px;
  color: #ffffffad;
  background: #353535;
  padding: 0 3px;
  border-radius: 2px;
  margin-left: 10px;
}
.content {
  display: block;
  height: 12px;
  line-height: 28px;
  font-size: 9.8px;
  color: #ffffffad;
  margin-bottom: 8px;
}
.right {
  position: absolute;
  bottom: 25px;
  right: 6%;
  font-size: 12px;
}
/* 底部消息 */
.more {
  position: absolute;
  width: 100%;
  height: 50px;
  line-height: 50px;
  font-size: 10px;
  text-align: center;
  color: #ffffffad;
}
</style>