<template>
  <!-- 首页视频模块 -->
  <view class="videoList">
    <view class="swiper-box">
      <swiper
        class="swiper"
        :vertical="true"
        @change="change"
        @touchstart="touchstart"
        @touchend="touchend"
      >
        <swiper-item v-for="(item, index) of videos" :key="item.id">
          <view class="swiper-item" style="color: #000">
            <video-player
              @changeClick="changeClick"
              ref="player"
              :video="item"
              :index="index"
              :tip="tip"
            ></video-player>
          </view>
          <view class="left-box">
            <list-left :item="item"></list-left>
          </view>
          <view class="right-box">
            <!-- 父组件调用子 ref  -->
            <list-right ref="right" :item="item"></list-right>
          </view>
        </swiper-item>
      </swiper>
    </view>
  </view>
</template>

<script>
import videoPlayer from "./videoPlayer.vue";
import listLeft from "./listLeft.vue";
import listRight from "./listRight.vue";
var time = null;
export default {
  // 接受父组件传递
  props: ["list","tip"],
  components: {
    videoPlayer,
    listLeft,
    listRight,
  },
  data() {
    return {
      videos: [],
      pageStartY: 0,
      pageEndY: 0,
      page: 0,
      cval: false,
    };
  },
  watch: {
    list() {
      this.videos = this.list;
    },
  },
  methods: {
    // 判断上下滑动 播放视频
    change(res) {
      clearTimeout(time);
      this.page = res.detail.current;

      time = setTimeout(() => {
        if (this.pageStartY > this.pageEndY) {
          // 向上滑动 视频下一个播放
          this.$refs.player[this.page].player();
          this.$refs.player[this.page - 1].pause();
          this.$emit("closeClick", this.cval);
          this.pageStartY = 0;
          this.pageEndY = 0;
        } else {
          this.$refs.player[this.page].player();
          this.$refs.player[this.page + 1].pause();
          this.pageStartY = 0;
          this.pageEndY = 0;
        }
      }, 1);
    },
    touchstart(res) {
      this.pageStartY = res.changedTouches[0].pageY;
    },
    touchend(res) {
      this.pageEndY = res.changedTouches[0].pageY;
    },
    // 双击点赞爱心
    changeClick() {
      // 调用子组件方法
      this.$refs.right[this.page].change();
    },
  },
};
</script>

<style>
.videoList {
  height: 92%;
  width: 100%;
  background-color: #000;
}
.swiper {
  height: 100%;
  width: 100%;
}
.swiper-box {
  
  height: 100%;
  width: 98%;
  margin: 0 1%;
}
.swiper-item {
  height: 100%;
  width: 100%;
  z-index: 19;
}
/* 左边子组件样式 */
.left-box {
  z-index: 20;
  position: absolute;
  bottom: 0px;
  left: 6px;
}
/* 右边子组件样式 */
.right-box {
  z-index: 20;
  position: absolute;
  bottom: 0px;
  right: 6px;
}
</style>