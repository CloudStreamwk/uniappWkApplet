<template>
<!-- 个人页面 -->
  <view class="personal">
      <personal-info></personal-info>
      <personal-list></personal-list>
      <tab :page="page"></tab>
  </view>
</template>

<script>

import personalInfo from "../../components/personalInfo.vue";
import personalList from "../../components/personalList.vue";
import tab from "../../components/tab.vue";
export default {
components:{
    personalInfo,
    personalList,
    tab
},
data(){
    return{
        page:"personal"
    }
}
}
</script>

<style>
.personal{
    width: 100%;
    height: 100%;
    background-color: #111218ee;
}
</style>