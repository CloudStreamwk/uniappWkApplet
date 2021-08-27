<template>
  <!-- 城市页面 -->
  <view class="city">
    <city-cicle :tcity="tcity"></city-cicle>
    <city-content :list="list"></city-content>
    <tab :page="page"></tab>
  </view>
</template>

<script>
import tab from "../../components/tab.vue";
import cityCicle from "../../components/cityCicle.vue";
import cityContent from "../../components/cityContent.vue";

export default {
  data() {
    return {
      list: [],
      tcity: "岳麓",
      page:"city"
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
  onShow() {
    uni.getStorage({
      key: "city",
      success: (res) => {
        this.tcity = res.data;
      },
    });
    uni.removeStorage({
      key: "city",
    });
  },

  components: {
    tab,
    cityCicle,
    cityContent,
  },
};
</script>

<style>
.city {
  width: 100%;
  background: #000;
}
</style>