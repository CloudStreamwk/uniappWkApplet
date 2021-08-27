<template>
  <!-- 首页的右边视频相关信息模块 -->
  <view class="listright">
    <view class="author-img">
      <image
        class="img"
        :src="'http://119.23.75.107/img/author/' + item.img"
      ></image>
      <view
        class="iconfont icon-jiahao add"
        @click="hide"
        v-show="show"
      ></view>
    </view>
    <view class="icon-box">
      <view
        class="iconfont icon-aixin_shixin right-box"
        :style="color"
        @click="changeColor"
      >
        <view class="number"> {{item.loveNumber}} </view>
      </view>
      <view class="iconfont icon-pinglun right-box">
        <view class="number"> {{item.commentNumber}} </view>
      </view>

      <view class="iconfont icon-zhifeiji right-box">
        <view class="number"> {{item.shareNumber}} </view>
      </view>
    </view>
    <view class="around">
      <image
        class="img"
        src="http://119.23.75.107/img/around_img.jpg"
      ></image>
    </view>
  </view>
</template>

<script>
export default {
  props: ["item"],
  data() {
    return {
      show: true,
      color: "",
    };
  },
  methods: {
    //   点击关注
    hide() {
      this.show = false;
    },
    // 点击点赞
    changeColor() {
      this.color = this.color === "" ? "color:red" : "";
    },
    // 双击点赞 通过父组件调用
    change() {
      this.color = "color:red";
    },
  },
};
</script>

<style>
.listright {
  width: 38px;
  margin: 0 auto;
}
/* 作者头像 */
.author-img {
  height: 38px;
  width: 38px;
  border-radius: 50%;
  border: 2px solid #fff;
  position: relative;
}
/* 关注图标样式 */
.add {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: red;
  position: absolute;
  bottom: -6px;
  left: 12px;
  text-align: center;
  line-height: 12px;
  color: #fff;
  font-size: 8px;
}
/* 点赞评论转发样式 */
.icon-box {

  margin-bottom: 15px;
}
.img {
  height: 38px;
  width: 38px;
  border-radius: 50%;
}
.right-box {
  position: relative;
  height: 20px;
  width: 38px;
  padding: 18px 0 10px 0px;
  text-align: center;
  line-height: 20px;
  color: #fff;
  font-size: 20px;
  margin: 0 auto;
}
.number {
  font-size: 10px;
  color: #fff;
}
.around {
  height: 38px;
  width: 38px;
  margin-bottom: 6px;
  animation: rotate 3s linear 0.2s infinite;
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>