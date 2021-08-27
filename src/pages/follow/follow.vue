<template>
  <!-- 关注页面 -->
  <view class="follow">
    <first-nav :page="page"></first-nav>

    <follow-header :close="close"></follow-header>

    <video-list
      :list="list"
      :tip="tip"
      @closeClick="closeClick"
    ></video-list>
    <tab></tab>
  </view>
</template>

<script>
import firstNav from "../../components/first-nav.vue";
import followHeader from "../../components/followHeader.vue";
import tab from "../../components/tab.vue";
import videoList from "../../components/videoList.vue";
export default {
  components: {
    firstNav,
    tab,
    videoList,
    followHeader,
  },
  data() {
    return {
      list: [],
      close: "",
      page: "follow",
      tip: false,
    };
  },
  onLoad(res) {
    this.getVideos();
    this.tip = res.tip;
  },
  methods: {
    getVideos() {
      uni.request({
        // 请求视频数据
        url: "http://119.23.75.107/api/videos.json",
        success: (res) => {
          this.list = res.data.list;
        },
      });
    },
    closeClick(res) {
      this.close = res;
    },
  },
};
</script>

<style>
.follow {
  width: 100%;
  height: 100%;
}
</style>
