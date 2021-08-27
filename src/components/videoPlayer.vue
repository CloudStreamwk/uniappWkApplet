<template>
  <!-- 首页视频播放模块 -->
  <view class="videoPlayer">
    <!-- objectFit 设置视频内容如何去适应 -->
    <video
      id="myVideo"
      class="video"
      :controls="false"
      :src="'http://119.23.75.107/video/' + video.src"
      :loop="true"
      :autoplay="autoplay"
      @click="click"
      objectFit="cover"
    ></video>
  </view>
</template>

<script>
var timer = null;
export default {
  props: ["video", "index", "tip"],
  data() {
    return {
      play: false,
      dblClick: false,
      autoplay: false,
    };
  },
  // 监听父组件 videos.json
  watch: {
    video() {
      console.log(this.video);
    },
  },
  methods: {
    // 单击为视频播放暂停 双击为点赞爱心
    click() {
      clearTimeout(timer);
      this.dblClick = !this.dblClick;
      timer = setTimeout(() => {
        if (this.dblClick) {
          if (this.play === false) {
            this.playThis();
          } else {
            this.pause();
          }
        } else {
          // 向父组件传递
          this.$emit("changeClick");
        }
        this.dblClick = false;
      }, 300);
    },
    // 播放和暂停
    player() {
      if (this.play === false) {
        this.videoContext.seek(0);
        this.videoContext.play();
        this.play = true;
      }
    },
    pause() {
      if (this.play === true) {
        this.videoContext.pause();
        this.play = false;
      }
    },
    playThis() {
      if (this.play === false) {
        this.videoContext.play();
        this.play = true;
      }
    },
    // 自动播放
    auto() {
      if (this.index === 0 && this.tip === "true") {
        this.autoplay = false;
        this.play = false;
      } else if (this.index === 0) {
        this.autoplay = true;
        this.play = true;
      }
    },
  },
  onReady() {
    this.videoContext = uni.createVideoContext("myVideo", this);
  },
  created() {
    this.auto();
  },
};
</script>

<style>
.videoPlayer {
  height: 100%;
  width: 100%;
  margin-top: 6%;
}
.video {
  height: 100%;
  width: 100%;
}
</style>