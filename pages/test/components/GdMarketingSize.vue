<template>
  <view class="GdMarketingSize">
    <view class="wrap" @click="showPopup">
      <text class="title">规格数量</text>
      <text class="choose">36, 123,123</text>
    </view>
    <uni-popup ref="popup" type="bottom">
      <view class="sizePopup">
        <view class="base">
          <image :src="logo" class="productImg"/>
          <view>
            <text class="productPrice">188888</text>
            <view>已选：36, 123,123</view>
          </view>
        </view>
        <view class="size">
          <view class="sizeItem">
            <view>
              <text class="sizeItemName">尺寸</text>
              <view class="sizeItemOption">
                <uni-data-checkbox mode="tag" v-model="value" :localdata="range" @change="change"></uni-data-checkbox>
              </view>
            </view>
          </view>
        </view>
        <view class="handle">
          <view class="addCart">加入购物车</view>
          <view class="buy">立即购买</view>
        </view>
      </view>
    </uni-popup>
  </view>
</template>
<script>
  import logo from "../../../static/logo.png"

  export default {
    name: "GdMarketingSize",
    data() {
      return {
        logo,
        value: 0,
				range: [{"value": 0,"text": "S"	},{"value": 1,"text": "M"},{"value": 2,"text": "L"},{"value": 3,"text": "XL"}]
      }
    },
    mounted() {
      this.$refs.popup.open('bottom');
    },
    methods: {
      showPopup() {
        this.$refs.popup.open('bottom');
      }
    },
  }
</script>
<style lang="less" scoped>
  .GdMarketingSize {
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
    .sizePopup {
      width: 100vw;
      height: 100vw;
      background-color: #FFFFFF;
      position: relative;
      .base {
        padding-left: 1.5rem;
        box-sizing: border-box;
        display: flex;
        margin-bottom: 3.8rem;
        .productImg {
          width: 10.5rem;
          height: 10.5rem;
          margin-top: -3rem;
          margin-right: 0.9rem;
        }
        .productPrice {
          display: block;
          padding-top: 2rem;
          font-size: 1.8rem;
          color: #D66377;
          margin-bottom: 1.4rem;
        }
      }
      .size {
        width: 100%;
        height: 20rem;
        background-color: blue;
        padding: 0 2rem;
        box-sizing: border-box;
      }
      .handle {
        position: absolute;
        bottom: 0;
        left: 0;
        height: 5rem;
        width: 100%;
        view {
          display: inline-block;
          width: 50%;
          line-height: 5rem;
          text-align: center;
          color: #FFFFFF;
          &.addCart {
            background-color: #B79F77;
            font-size: 1.6rem;
          }
          &.buy {
            background-color: #333333;
            font-size: 1.6rem;
          }
        }
      }
    }
  }
</style>