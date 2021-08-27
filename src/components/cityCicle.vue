<template>
  <!-- 城市模块 -->
  <view>
    <view class="cityCicle">
      <navigator
        open-type="navigate"
        class="cityregion"
        url="/pages/changeCity/changeCity"
        animation-type="side-in-bottom"
        animation-duration="300"
      >
        <view class="reginon">{{ tcity }}</view>
        <view class="iconfont icon-jiantouarrow486"></view>
      </navigator>
      <view class="conlation">
        <view class="conlation-left con">
          <view class="icon">
            <view class="iconfont icon-ditu"></view>
          </view>
          <view class="bigfont">地图</view>
          <view class="smallfont">发现本地新鲜事</view>
        </view>
        <view class="conlation-right con">
          <view class="icon">
            <view class="iconfont icon-quanzi"></view>
          </view>
          <view class="bigfont">同城圈子</view>
          <view class="smallfont">进圈子交朋友</view>
        </view>
      </view>
    </view>
    <view class="ground"> </view>
  </view>
</template>

<script>
export default {
  props: ["tcity"],

  data() {
    return {

    };
  },

};
</script>

<style>
.cityCicle {
  width: 92%;
  padding: 0 4%;
  position: fixed;
  top: 0;
  left: 0;
  color: #fff;
  z-index: 19;
  background-color: #000;
}
.ground {
  width: 100%;
  height: 110px;
}
/* 当前城市 */
.cityregion {
  margin-top: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 15px;
  z-index: 19;
}
/* 城市圈子交友 */
.conlation {
  width: 100%;
  height: 50px;
  position: relative;
  z-index: 18;
  margin-top: 5px;
}
.con {
  position: absolute;
  top: 8px;
  width: 49%;
  height: 30px;
  background: #424242;
  display: flex;
  border-radius: 2px;
}
.conlation-left {
  left: 0px;
}
.conlation-right {
  right: 0px;
}
/* 城市交友圈子图标 */
.icon {
  width: 17px;
  height: 17px;
  border-radius: 50%;
  background-color: #1d1c1d;
  color: #f5b400;
  align-self: center;
  margin: 5px;
}
.icon .iconfont {
  text-align: center;
  font-size: 14px;
}
/* 城市交友圈子文字部分 */
.bigfont {
  height: 30px;
  line-height: 30px;
  font-size: 13px;
  margin: 0px 2px;
}
.smallfont {
  height: 30px;
  line-height: 34px;
  font-size: 9px;
  color: #b4b4b4;
}
</style>