<template>
  <!-- 个人主页模块 -->
  <view class="personalInfo">
    <view class="background-img-box">
      <image
        class="background-img"
        src="http://119.23.75.107/img/background-img.jpg"
      ></image>
    </view>
    <view class="top">
      <view class="personal-img-box">
        <image
          class="personal-img"
          src="http://119.23.75.107/img/background-img.jpg"
        ></image>
      </view>
      <navigator
        class="change"
        open-type="navigate"
        url="/pages/changeInfo/changeInfo"
      >
        编辑资料
      </navigator>
      <view class="friend-box">
        <view class="iconfont icon-jiahao add"></view>
        <view class="friend">朋友</view>
      </view>
    </view>
    <view class="name-box">
      <view class="name">lyhy</view>
      <view class="douyinId">抖音号:12.2.21</view>
    </view>
    <view class="text-box">
      <view class="introduce">
        空
      </view>
      <view class="label-box">
        <view class="label">18岁</view>
        <view class="label">长沙</view>
      </view>
      <view class="number-box">
        <view class="nbox">
          <text class="number">0</text>
          <text class="number-text">获赞</text>
        </view>
        <view class="nbox">
          <text class="number">43</text>
          <text class="number-text">关注</text>
        </view>
        <view class="nbox">
          <text class="number">8</text>
          <text class="number-text">粉丝</text>
        </view>
      </view>
      <view class="add-shop">
        <view class="icon-box">
          <view class="iconfont icon-gouwuchekong shopicon"></view>
        </view>
        <view class="shop-text">
          <view class="shop-title">抖音商城</view>
          <view class="shop-con">发现超值好物</view>
        </view>
      </view>

    </view>
    <view class="option-box">
      <view
        class="option"
        :style="style"
      >作品</view>
      <view class="option">私密</view>
      <view class="option">喜欢</view>
      <view class="option">收藏</view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      style: "color:#fff;border-bottom: 2px solid #f3f035;",
    };
  },
};
</script>

<style>
.personalInfo {
  width: 100%;
}
/* 背景样式 */
.background-img-box {
  width: 98%;
  padding: 0 1%;
  z-index: 18;
  height: 130px;
}
.background-img {
  width: 100%;
  height: 100%;
}
/* 头像组件样式 */
.top {
  width: 100%;
  position: absolute;
  top: 90px;
  left: 0;
  z-index: 19;
  height: 50px;
  background-color: #1e2029;
}
.personal-img-box {
  margin: -15px 0 0 5%;
}
.personal-img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  border: 3px solid #000;
}
.change {
  position: absolute;
  top: 8px;
  right: 26%;
  width: 45%;
  height: 28px;
  line-height: 28px;
  color: #fff;
  text-align: center;
  font-size: 11.5px;
  background: #424242;
  border-radius: 2px;
  letter-spacing: 1px;
}
.friend-box {
  position: absolute;
  top: 8px;
  right: 4%;
  width: 20%;
  height: 28px;
  line-height: 24px;
  color: #fff;
  text-align: center;
  background: #424242;
  border-radius: 2px;
  letter-spacing: 1px;
}
.add {
  display: inline;
  font-size: 11.5px;
}
.friend {
  display: inline;
  font-size: 11.5px;
}
/* 用户名 */
.name-box {
  margin: 0 5%;
  color: #fff;
  margin-top: 15px;
  border-bottom: 1px solid #5a5a5a69;
  letter-spacing: 1px;
}
.name {
  height: 30px;
  line-height: 30px;
  font-size: 18px;
}
.douyinId {
  height: 30px;
  line-height: 30px;
  font-size: 10px;
  margin-bottom: 6px;
  color: #ffffffa9;
}
/* 签名信息 */
.text-box {
  padding: 0 5%;
  margin-top: 10px;
}
.introduce {
  height: 20px;
  line-height: 20px;
  font-size: 12px;
  color: #fff;
}
.label-box {
  width: 100%;
  height: 20px;
  line-height: 20px;
  color: #ffffffa9;
}
.label {
  height: 18px;
  padding: 0 4px;
  line-height: 18px;
  font-size: 9px;
  float: left;
  background: #353535;
  border-radius: 2px;
  margin-right: 5px;
}
/* 获赞数量 */
.number-box {
  width: 100%;
  height: 30px;
  line-height: 30px;
}
.nbox {
  height: 30px;
  line-height: 30px;
  float: left;
  margin-right: 10px;
}
.number {
  color: #fff;
  font-size: 14.5px;
  margin-right: 2px;
}
.number-text {
  color: #ffffffa9;
  line-height: 36px;
  font-size: 12px;
  letter-spacing: 1px;
}
/* 商城样式 */
.add-shop {
  height: 40px;
  width: 100%;
  color: #fff;
  margin: 10px 0;
}
.icon-box {
  height: 35px;
  line-height: 35px;
  width: 35px;
  text-align: center;
  background: #353535d7;
  border-radius: 5px;
  float: left;
  margin-right: 8px;
}
.shop-text {
  display: inline;
  height: 35px;
  letter-spacing: 0.6px;
}
.shop-title {
  font-size: 12.5px;
}
.shop-con {
  font-size: 9px;
  margin-top: 4px;
  color: #ffffffa9;
}
/* 作品喜欢样式 */
.option-box {
  width: 98%;
  height: 40px;
  line-height: 40px;
  margin: 0 1%;
}
.option {
  width: 25%;
  height: 40px;
  line-height: 40px;
  color: #ffffffa9;
  float: left;
  text-align: center;
  letter-spacing: 1px;
}
</style>