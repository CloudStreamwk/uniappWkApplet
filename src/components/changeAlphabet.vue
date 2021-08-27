<template>
  <!-- 切换城市右边字母列表模块 -->
  <view class="changeAlphabet">
    <view class="list">
      <view class="iconfont icon-jiantouarrow492 jicon"></view>
      <view
        class="item"
        v-for="(item, index) of lcity"
        :key="index"
        hover-class="hover"
        @click="click(item.initial)"
        @touchstart="touchMtart"
        @touchmove="touchMove"
        @touchend="touchEnd"
      >
        {{ item.initial }}
      </view>
    </view>
  </view>
</template>

<script>
var time = null;
export default {
  props: ["lcity"],
  data() {
    return {
      touch: false,
    };
  },
  methods: {
    // 点击传值当前字母
    click(res) {
      this.$emit("change", res);
    },
    touchMtart() {
      this.touch = true;
    },
    touchMove(e) {
      clearTimeout(time);
      time = setTimeout(() => {
        if (this.touch) {
          const touchY = e.changedTouches[0].pageY - 177;
          const index = Math.floor(touchY / 12);
          if (index >= 0 && index < this.lcity.length) {
            this.$emit("change", this.lcity[index].initial);
          }
        }
      }, 30);
    },
    touchEnd() {
        this.touch = false;
    },
  },
};
</script>

<style>
.changeAlphabet {
  position: fixed;
  top: 165px;
  right: 0px;
  z-index: 20;
}
.list {
  width: 20px;
}
.jicon {
  text-align: center;
  line-height: 12px;
  font-size: 12px;
  color: #cccccce1;
}
.item {
  text-align: center;
  line-height: 12px;
  font-size: 8px;
  color: #cccccce1;
}
/* 点击样式 */
.hover {
  text-align: center;
  line-height: 12px;
  font-size: 12px;
  color: #cccccce1;
}
</style>