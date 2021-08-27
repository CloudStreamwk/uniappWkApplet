<template>
<!-- 切换城市页面 -->
  <view class="changeCity">
    <changer-herder></changer-herder>
    <change-list :letter="letter" :list="list" :lcity="lcity"></change-list>
    <change-alphabet @change="change" :lcity="lcity"> </change-alphabet>
  </view>
</template>

<script>
import changerHerder from "../../components/changerHerder.vue";
import changeList from "../../components/changeList.vue";
import changeAlphabet from "../../components/changeAlphabet.vue";
export default {
  data() {
    return {
      list: [],
      lcity: [],
      letter: [],
    };
  },
  created() {
    this.getVideos();
    this.getCityInfo();
  },
  methods: {
    getCityInfo() {
      uni.request({
        // 请求全国城市数据
        url: "http://119.23.75.107/api/city.json",
        success: (e) => {
          this.lcity = e.data.city;
        },
      });
    },
    getVideos() {
      uni.request({
        // 请求热门城市数据
        url: "http://119.23.75.107/api/hotcity.json",
        success: (res) => {
          this.list = res.data.list;
        },
      });
    },
    change(res) {
      this.letter = res;
    },
  },
  components: {
    changerHerder,
    changeList,
    changeAlphabet,
  },
};
</script>

<style>
.changeCity {
  width: 100%;
  height: 100%;
  background-color: #252525;
}
</style>