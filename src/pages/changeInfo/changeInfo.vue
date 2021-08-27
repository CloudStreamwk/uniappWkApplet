<template>
  <!-- 编辑信息页面 -->
  <view
    class="changeInfo"
  >
    <view class="nav-box">
      <navigator
        open-type="navigateBack"
        delta="1"
        class="iconfont icon-jiantou-copy icon-nav"
      ></navigator>
      <view class="title">编辑资料</view>
    </view>
    <view class="box">
      <view class="img-box">
        <view
          class="change-img"
          @click="chooseImg"
        >
          <image
            class="img"
            :src="src"
          ></image>
          <view class="iconfont icon-xiangji icon-canera"></view>
        </view>
        <view class="text">
          点击更换头像
        </view>
      </view>
    </view>
    <view class="info-box">
      <navigator
        open-type="redirect"
        url="/pages/modify/modify"
        class="text-box"
      >
        <view class="left">名字</view>
        <view class="iconfont icon-arrow-right icon-box"></view>
        <view class="right">{{user.userName}}</view>
      </navigator>
      <!-- 页面传参，v-if switch渲染，onload接受数据 -->
      <view class="text-box">
        <view class="left">抖音号</view>
        <view class="iconfont icon-arrow-right icon-box"></view>
        <view class="right">12.2.21</view>
      </view>
      <view class="text-box">
        <view class="left">简介</view>
        <view class="iconfont icon-arrow-right icon-box"></view>
        <view class="right">空</view>
      </view>
      <view
        class="text-box"
        @click="showPicker"
      >
        <view class="left">性别</view>
        <view class="iconfont icon-arrow-right icon-box"></view>
        <view class="right">{{user.sex}}</view>
      </view>
      <view class="text-box">
        <view class="left">生日</view>
        <view class="iconfont icon-arrow-right icon-box"></view>
        <view class="right">点击设置</view>
      </view>
      <view class="text-box">
        <view class="left">所在地</view>
        <view class="iconfont icon-arrow-right icon-box"></view>
        <view class="right">中国·湖南·长沙</view>
      </view>
      <view class="text-box">
        <view class="left">学校</view>
        <view class="iconfont icon-arrow-right icon-box"></view>
        <view class="right">点击设置</view>
      </view>
      <view class="text-box">
        <view class="left">头像挂件</view>
        <view class="iconfont icon-arrow-right icon-box"></view>
        <view class="right">设置头像挂件</view>
      </view>
    </view>
    <view
      class="pick"
      v-show="pickShow"
    >
      <picker-view
        class="picker-view"
        @change="bindSexChange"
        :style="pickStyle"
      >
        <view
          class="pick-left"
          @click="hidePicker"
        >取消</view>
        <view
          class="pick-right"
          @click="deterPicker"
        >确定</view>
        <picker-view-column class="picker-column">
          <view
            class="column"
            v-for="(item,index) of sex"
            :key="index"
          >{{item}}</view>
        </picker-view-column>
      </picker-view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      src: "http://119.23.75.107/img/background-img.jpg",
      user: {
        userName: "lyhy",
        sex: "男",
      },
      sex: ["男", "女", "不展示"],
      pickShow: false,
      pickStyle: "",
    };
  },
  methods: {
    chooseImg() {
      uni.chooseImage({
        count: 1,
        sourceType: ["album"],
        sizeType: ["original", "compressed"],
        success: (res) => {
          this.src = res.tempFilePaths;
        },
      });
    },
    // 选择框触发change事件
    bindSexChange(e) {
      uni.setStorage({
        key: "sex",
        data: this.sex[e.target.value],
      });
    },
    deterPicker() {
      uni.getStorage({
        key: "sex",
        success: (res) => {
          this.user.sex = res.data;
        },
      });
      this.hidePicker();
    },
    // 显示性别选择框
    showPicker() {
      if (this.pickShow === false) {
        this.pickShow = true;
      }
      uni.setStorage({
        key: "sex",
        data: this.sex[0],
      });
    },
    // 关闭性别选择框
    hidePicker() {
      if (this.pickShow === true) {
        this.pickShow = false;
      }
    },
  },
  onLoad() {
    uni.getStorage({
      key: "newName",
      success: (res) => {
        this.user.userName = res.data;
      },
    });
    uni.getStorage({
      key: "sex",
      success: (res) => {
        this.user.sex = res.data;
      },
    });
  },
};
</script>

<style>
.changeInfo {
  width: 92%;
  height: 100%;
  padding: 0 4%;
  background-color: #111218ee;
  z-index: 18;
}
/* 顶部 */
.nav-box {
  height: 60px;
  position: relative;
  margin: 0 auto;
}
.title {
  text-align: center;
  font-size: 12px;
  letter-spacing: 1px;
  line-height: 80px;
  color: #ffffffdc;
}
.icon-nav {
  position: absolute;
  top: 30px;
  font-size: 16px;
  color: #ffffffdc;
}
/* 更换头像 */
.box {
  width: 100%;
  height: 110px;
  margin: 0 auto;
  /* border: 1px solid #fff; */
}
.img-box {
  width: 24%;
  text-align: center;
  position: relative;
  margin: 0% 38%;
}
.change-img {
  margin-top: 18px;
  width: 100%;
  height: 100%;
}
.img {
  width: 65px;
  height: 65px;
  border-radius: 50%;
  float: left;
}
.text {
  position: absolute;
  color: #fff;
  font-size: 11px;
  top: 65px;
  letter-spacing: 0.5px;
  height: 40px;
  line-height: 40px;
}
.icon-canera {
  position: absolute;
  float: left;
  width: 65px;
  height: 65px;
  border-radius: 50%;
  background: #353535ab;
  line-height: 70px;
  font-size: 25px;
  color: #ffffff;
}
/* 具体资料显示样式 */
.text-box {
  width: 100%;
  height: 40px;
  line-height: 40px;
  letter-spacing: 0.5px;
}
.left {
  float: left;
  font-size: 12px;
  color: #ffffff;
}
.right {
  float: right;
  font-size: 12px;
  margin-right: 7px;
  color: #ffffffa9;
}
.icon-box {
  float: right;
  font-size: 12px;
  width: 10px;
  color: #ffffffa9;
}
/* 滚动选择框 */
.pick {
  position: fixed;
  bottom: 0px;
  left: 0px;
  color: #000;
  width: 100%;
  height: 30%;
}
.picker-view {
  background: #ccc;
  width: 100%;
  height: 100%;
  border-radius: 30px 30px 0 0;
}
.picker-column {
  text-align: center;
  border-radius: 30px 30px 0 0;
  z-index: 18;
}
.pick-left {
  position: absolute;
  left: 15px;
  top: 10px;
  z-index: 19;
}
.pick-right {
  position: absolute;
  right: 15px;
  top: 10px;
  z-index: 19;
  color: #4db87f;
}
.column {
  font-size: 14px;
  height: 20px;
  line-height: 30px;
}
</style>