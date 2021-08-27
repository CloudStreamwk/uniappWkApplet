<template>
  <!-- 消息页面 -->
  <view class="news">
    <news-nav></news-nav>
    <news-content :list="list"></news-content>
    <tab :page="page"></tab>
  </view>
</template>

<script>
import newsNav from "../../components/newsNav.vue";
import newsContent from "../../components/newsContent.vue";
import tab from "../../components/tab.vue";
export default {
  data() {
    return {
        list:[],
        page:"news"
    };
  },
  components: {
    newsNav,
    newsContent,
    tab,
  },
  onLoad() {
    this.getVideos();
  },
  methods: {
    getVideos() {
      uni.request({
        // 请求视频数据
        url: "http://119.23.75.107/api/message.json",
        success: (res) => {
          this.list = res.data.list;
        },
      });
    },
  },
};
</script>

<style>
.news {
  height: 100%;
  width: 100%;
}
</style>