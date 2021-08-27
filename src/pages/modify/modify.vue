<template>
  <!-- 修改名字模块 -->
  <view class="modify">
    <view class="nav-box">
      <navigator
        open-type="redirect"
        url="/pages/changeInfo/changeInfo"
        class="iconfont icon-jiantou-copy icon-nav"
      ></navigator>
      <view class="title">修改名字</view>
    </view>
    <view class="box">
      <view class="text">我的名字</view>
      <view class="input-name">
        <input
          class="input"
          type="text"
          v-model="name"
          maxlength="20"
        >
        <view
          class="iconfont icon-cuowu delete"
          @click="deleteAll"
        ></view>
        <view class="number">
          {{name.length}}/20
        </view>
      </view>
    </view>
    <view
      class="footer"
      @click="click(name)"
      :style="style"
    >
      保存
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      name: "lyhy",
      style: "",
    };
  },
  watch: {
    name() {
      if (this.name.length === 0) {
        this.style = "color: #ffffffa9;background: #353535d7;";
      } else {
        this.style = "color: #ffffffdc;background: #5a5a5a69;";
      }
    },
  },
  methods: {
    deleteAll() {
      this.name = "";
    },
    click(res) {
      if (res === "" || res === null) {
        this.name = "请输入你的昵称";
      } else {
        uni.setStorage({
          key: "newName",
          data: res,
        });
        uni.redirectTo({
          url: "/pages/changeInfo/changeInfo",
        });
      }
    },
  },
  onShow(){
      uni.getStorage({
      key: "newName",
      success: (res) => {
        this.name = res.data;
      },
    });
  }
};
</script>

<style>
.modify {
  width: 100%;
  height: 100%;
  background-color: #111218ee;
}
/* 顶部 */
.nav-box {
  height: 60px;
  width: 92%;
  padding: 0 4%;
  position: relative;
  margin: 0 auto;
  border-bottom: 1px solid #5a5a5a69;
}
.title {
  text-align: center;
  font-size: 15px;
  letter-spacing: 0.5px;
  line-height: 80px;
  color: #ffffff;
}
.icon-nav {
  position: absolute;
  top: 30px;
  font-size: 16px;
  color: #ffffffdc;
}
/* 修改框样式 */
.box {
  width: 92%;
  margin: 0 4%;
}
.text {
  color: #ffffffa9;
  font-size: 10px;
  letter-spacing: 1px;
  height: 30px;
  line-height: 30px;
  margin-top: 10px;
}
.input-name {
  font-size: 12px;
  position: relative;
}
.input {
  width: 80%;
  color: #ffffffdc;
  height: 30px;
  line-height: 30px;
}
.delete {
  position: absolute;
  right: 0;
  top: 8px;
  height: 15px;
  width: 15px;
  line-height: 15px;
  font-size: 8px;
  color: #000;
  background: #ffffffa9;
  border-radius: 50%;
  text-align: center;
}
.number {
  color: #ffffffa9;
  font-size: 10px;
  height: 30px;
  line-height: 30px;
  border-top: 1px solid #5a5a5a69;
}
/* 确定按钮 */
.footer {
  width: 92%;
  margin: 2% 4%;
  text-align: center;
  font-size: 14px;
  color: #ffffffdc;
  height: 30px;
  line-height: 30px;
  border-radius: 2px;
  background: #5a5a5a69;
}
</style>