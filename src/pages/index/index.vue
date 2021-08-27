<template>
  <!-- 首页页面 -->
  <view class="content">
    <first-nav :page="page"></first-nav>
    <video-list
      :list="list"
    ></video-list>
    <tab :page="page"></tab>
  </view>
</template>

<script>
import tab from "../../components/tab.vue";
import firstNav from "../../components/first-nav.vue";
import videoList from "../../components/videoList.vue";
export default {
  data() {
    return {
      list: [],
      page: "recommend",
    };
  },
  onLoad() {
    this.getVideos();
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
  },
  components: {
    tab,
    firstNav,
    videoList,
  },
};
</script>

<style>
.content {
  height: 100%;
  width: 100%;
}
</style>
