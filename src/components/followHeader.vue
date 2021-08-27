<template>
  <!-- 关注模块 -->
  <view class="box">
    <view class="followHeader" :style="shead">
      <view class="followOften" v-show="show"> 常看的人(1) </view>
      <view class="follist" v-show="show">
        <view class="folPop">
          <image class="folImg" src="http://119.23.75.107/img/author/1-1.jpg"> </image>
          <view class="folName">威朗普</view>
        </view>
      </view>
      <view class="boxclose" :style="sclose">
        <view class="close" @click="tipChange">
          <view class="tips">{{ tip }} </view>
          <view :class="icon"></view>
        </view>
      </view>
    </view>
    <view class="ground" v-show="show"> </view>
  </view>
</template>

<script>
export default {
  props: ["close"],

  data() {
    return {
      show: true,
      sclose: "margin-top: 20px;",
      icon: "iconfont icon-jiantouarrow492 del",
      tip: "上滑关闭",
      shead: "background-color: #5154682d;",
    };
  },
  watch: {
    close() {
      this.show = this.close;
      this.shead = "";
    },
  },
  methods: {
    //   点击打开关注的博主，关闭显示博主视频页面
    tipChange() {
      if (this.show === true) {
        this.show = false;
        this.sclose = "margin-top: 20px;";
        this.icon = "iconfont icon-jiantouarrow486 del";
        this.tip = "直播/常看的人";
        this.shead = "";
      } else {
        this.show = true;
        this.sclose = "margin-top: 20px;";
        this.icon = "iconfont icon-jiantouarrow492 del";
        this.tip = "上滑关闭";
        this.shead = "background-color: #51546849;";
      }
    },
  },
};
</script>

<style>
.box {
  width: 100%;
  padding: 0px 1%;
  background-color: #000;
}
.followHeader {
  position: fixed;
  top: 56px;
  width: 98%;
  height: 80px;
  z-index: 19;
  color: #ccc;
  margin-top: 8px;
  padding: 4px 0px;
}
.ground {
  width: 100%;
  height: 150px;
}
/* 关注的人 */
.followOften {
  height: 15px;
  line-height: 15px;
  font-size: 10px;
  letter-spacing: 0.5px;
  margin-left: 7px;
}
.follist {
  margin-top: 5px;
}
.folPop {
  width: 20%;
  text-align: center;
}
/* 头像 */
.folImg {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
.folName {
  height: 15px;
  line-height: 15px;
  font-size: 10px;
}
/* 关闭提示 */

.boxclose {
  position: relative;
  width: 100%;
  text-align: center;
}
.close {
  display: inline-block;
  background-color: #74727262;
  padding-right: 20px;
  padding-left: 10px;
  border-radius: 10%;
  height: 16;
  line-height: 16px;
}
.tips {
  display: inline-block;
  letter-spacing: 1px;

  font-size: 10px;
}
.del {
  position: absolute;
  display: inline-block;

  font-size: 13px;
  top: 5px;
}
</style>