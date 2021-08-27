<template>
  <!-- 城市视频模块 -->
  <scroll-view
    class="scrolly"
    scroll-y="true"
    @touchstart="touchstart"
    @touchend="touchend"
    @change="change"
  >
    <view
      class="item"
      v-for="(item, index) of videos"
      :key="item.id"
    >
      <view
        class="video"
        @click="clickPlay(videos)"
      >
        <video
          style="width: 100%; height: 100%"
          controls
          play-btn-position="center"
          :show-fullscreen-btn="false"
          :src="'http://119.23.75.107/video/' + item.src"
        ></video>
      </view>
      <view class="img">
        <img
          class="img-box"
          :src="'http://119.23.75.107/img/author/' + item.img"
        />
      </view>
    </view>

  </scroll-view>

</template>

<script>
export default {
  props: ["list"],
  data() {
    return {
      videos: [],
      pageStartY: 0,
      pageEndY: 0,
    };
  },
  watch: {
    list() {
      this.videos = this.list;
    },
  },
  methods: {
    change() {
      if (this.pageStartY - this.pageEndY > 50) {
        this.pageStartY = 0;
        this.pageEndY = 0;
      } else {
        // 向上滑动
        this.pageStartY = 0;
        this.pageEndY = 0;
      }
    },
    touchstart(res) {
      this.pageStartY = res.changedTouches[0].pageY;
    },
    touchend(res) {
      this.pageEndY = res.changedTouches[0].pageY;
    },
    // 点击视频进入视频详情页面
    clickPlay(res) {
      console.log(res);
      uni.setStorage({
        key: "videoList",
        data: res,
      });
      uni.navigateTo({
        url: "/pages/player/player",
      });
    },
  },
};
</script>

<style>
.videolist {
  height: 100%;
  width: 100%;
  padding: 8px 0 50px 0;
  background-color: #000;
  z-index: 18;
}

/* 视频样式 */
.item {
  width: 50%;
  float: left;
  height: 280px;
  position: relative;
  background-color: #000;
  padding-bottom: 5px;
  z-index: 18;
}
.video {
  width: 96%;
  height: 280px;
  margin-left: 2%;
  z-index: 18;
}
/* 头像样式 */
.img {
  position: relative;
  bottom: 40px;
  left: 10px;
  z-index: 18;
  width: 25%;
}
.img .img-box {
  width: 30px;
  height: 30px;
  border-radius: 50%;
}
</style>