<template>
  <view class="GdMarketingSize">
    <view class="wrap" @click="showPopup">
      <text class="title">规格数量</text>
      <text class="choose">36, 123,123</text>
    </view>
    <uni-popup ref="popup" type="bottom">
      <view class="sizePopup">
        <view class="base">
          <image :src="sizeOriginArr[value].dataPic" class="productImg"/>
          <view>
            <text class="productPrice">{{sizeOriginArr[value].pricesetNprice}}</text>
            <view>已选：{{sizeArr[value].text}}</view>
          </view>
        </view>
        <view class="size">
          <view class="sizeItems">
            <view class="sizeItem">
              <view class="sizeItemName">尺寸</view>
              <view class="sizeItemOption">
                <uni-data-checkbox mode="tag" selectedColor="#B79F77" v-model="value" :localdata="sizeArr" @change="change"></uni-data-checkbox>
              </view>
            </view>
          </view>
          <view class="account">
            <view class="accountName">数量</view>
            <view class="accountValue">
              <uni-number-box></uni-number-box>
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
    props: ['goodsDetail'],
    data() {
      return {
        logo,
        value: 0,
        choosenArr: [],
        sizeArr: [],
        sizeOriginArr: []
      }
    },
    mounted() {
      // console.log(62, this.goodsDetail)
    },
    watch: {
      goodsDetail: function(val) {
        const aim = val?.rsSkuDomainList;
        const result = [];
        for (const [index, item] of aim?.entries()) {
          result[index] = {
            "value": index,
            "text": item.skuName
          }
        }
        this.sizeArr = result;
        this.sizeOriginArr = aim;
        console.log(this.sizeOriginArr)
      }
    },
    methods: {
      showPopup() {
        this.$refs.popup.open('bottom');
      },
      change(e) {
        console.log(60, e);
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
        // background-color: blue;
        padding: 0 2rem;
        box-sizing: border-box;
        .sizeItems {
          margin-bottom: 2.8rem;
          .sizeItem {
            display: flex;
            .sizeItemName {
              font-size: 1.4rem;
              margin-right: 2.3rem;
              color: #333333;
              width: 3.5rem;
              padding-top: 0.7rem;
              flex-shrink: 0;
            }
          }
        }
        .account {
          display: flex;
          .accountName {
            font-size: 1.4rem;
            width: 3.5rem;
            margin-right: 2.3rem;
            color: #333333;
          }
        }
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