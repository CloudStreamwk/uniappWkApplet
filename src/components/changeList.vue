<template>
  <!-- 切换城市内容模块 -->
  <view class="changeList">
    <scroll-view class="scrolly" scroll-y="true" :scroll-into-view="viewId">
      <view class="city-box">
        <view class="box">
          <view class="title"> 自动定位 </view>
          <view class="cuttentCity"> {{ tcity }} </view>
        </view>

        <view class="box">
          <view class="title"> 热门城市</view>
          <view class="hotlist">
            <view
              class="item"
              v-for="(item, index) of list"
              :key="item.id"
              
            >
              {{ item.name }}
            </view>
          </view>
        </view>
        <!-- 字母查找城市 -->
        <view class="box-list" v-for="(city, index) of lcity" :key="city.id">
          <view class="initial" :id="city.initial">
            {{ city.initial }}
          </view>
          <view
            class="city-name"
            v-for="(cities, index) of city.list"
            :key="cities.code"
            @click="click(cities.name)"
          >
            {{ cities.name }}
          </view>
        </view>
      </view>
    </scroll-view>
  </view>
</template>

<script>
export default {
  props: ["list", "lcity", "letter"],
  data() {
    return {
      viewId: "",
      tcity: "岳麓",
    };
  },
  watch: {
    letter() {
      // 当字母列表滚动时，通过viewId绑定 scroll-view标签内的ID
      this.viewId = this.letter;
    },
  },
  methods: {
    // 异步缓存，跳转到所点击城市页面
    click(res) {
      uni.setStorage({
        key: "city",
        data: res,
      });
      uni.getStorage({
        key: "city",
        success: (res) => {
          this.tcity = res.data;
        },
      });
      uni.switchTab({
        url: "/pages/city/city",
      });
    },
  },
};
</script>

<style>
.changeList {
  height: 100%;
  width: 90%;
  color: #fff;
  padding: 0 5%;
  background-color: #252525;
  z-index: 19;
}
.box {
  margin-top: 6px;
  border-bottom: 1px solid #5a5a5a69;
}
/* 当前城市和热门城市 */
.title {
  height: 30px;
  line-height: 30px;
  font-size: 11px;
}
.cuttentCity {
  font-size: 12px;
  color: #ccc;
  height: 30px;
  line-height: 30px;
}
.hotlist {
  width: 100%;
  overflow: hidden;
  margin-bottom: 10px;
}
/* 热门城市渲染 */
.item {
  width: 30%;
  height: 30px;
  line-height: 30px;
  font-size: 10px;
  background-color: #353535;
  color: #ccc;
  margin-bottom: 8px;
  margin-right: 8px;
  text-align: center;
  float: left;
}
/* 字母查找城市 */
.box-list {
  padding: 8px 5px;
}
.initial {
  height: 25px;
  line-height: 25px;
  font-size: 11px;
}
.city-name {
  height: 35px;
  line-height: 35px;
  font-size: 11px;
  border-bottom: 1px solid #5a5a5a69;
  letter-spacing: 1px;
}
.scrolly {
  height: 100%;
}
</style>