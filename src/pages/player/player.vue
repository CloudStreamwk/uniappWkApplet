<template>
  <view class="player">
    <navigator
      class="iconfont icon-jiantou-copy icon-nav"
      open-type="navigateBack"
      delta="1"
    ></navigator>
    <input
      type="text"
      class="footer"
      placeholder="留下你的精彩评论吧"
    ></input>
    <video-list :list="list"></video-list>
  </view>
</template>

<script>
import videoList from "../../components/videoList.vue";
export default {
  data() {
    return {
      list: "",
    };
  },
  components: {
    videoList,
  },
  methods: {},
  onLoad() {
    uni.getStorage({
      key: "videoList",
      success: (res) => {
        this.list = res.data;
      },
    });
  },
};
</script>

<style>
.player {
  position: relative;
  width: 100%;
  height: 100%;
  background: #000;
}

.icon-nav {
  position: absolute;
  z-index: 18;
  top: 30px;
  left: 4%;
  font-size: 20px;
  color: #ffffff;
}
.footer {
  position: absolute;
  bottom: 0px;
  left: 0px;
  height: 8%;
  width: 92%;
  margin: 0 4%;
  font-size: 13px;
  letter-spacing: 0.5px;
  color: #fff;
}
</style>