<template>
  <view class="GdMarketingPromotion">
    <view class="wrap" @click="showPopup">
      <text class="title">规格数量</text>
      <text class="choose">36, 123,123</text>
    </view>
  </view>
</template>
<script>
  export default {
    name: "GdMarketingPromotion"
  }
</script>
<style lang="less" scoped>
  .GdMarketingPromotion {
    .wrap {
      border-top: 1px solid #EDEDED;
      border-bottom: 1px solid #EDEDED;
      height: 5.3rem;
      line-height: 5.3rem;
      display: flex;
      justify-content: space-between;
      .title {
        font-size: 1.3rem;
        color: #999999;
      }
      .choose {
        color: #333333;
        font-size: 1.3rem;
      }
    }
  }
</style>