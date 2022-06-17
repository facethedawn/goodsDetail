<template>
	<page-meta root-font-size="62.5%">
		<view class="goodsDetail">
      <GdSwiper :goodsDetail = "goodsDetail"/>
      <div class="wrap">
				<GdTitle :goodsDetail = "goodsDetail"/>
        <GdPrice :goodsDetail = "goodsDetail"/>
        <GdMarketingSize/>
        <GdMarketingPromotion/>
        <GdMarketingCoupon/>
      </div>
      <GdComment/>
      <GdIntro :goodsDetail = "goodsDetail"/>
      <view class="safe" v-if="needSafe"></view>
      <GdFooter/>
		</view>
	</page-meta>
</template>

<script>
import GdSwiper from './components/GdSwiper.vue';
import GdTitle from './components/GdTitle.vue';
import GdPrice from './components/GdPrice.vue';
import GdMarketingSize from './components/GdMarketingSize.vue';
import GdMarketingPromotion from './components/GdMarketingPromotion.vue';
import GdMarketingCoupon from './components/GdMarketingCoupon.vue';
import GdComment from './components/GdComment.vue';
import GdIntro from './components/GdIntro.vue';
import GdFooter from './components/GdFooter.vue';

import "../../common/style/iconfont.css";


export default {
  data() {
    return {
      url: "https://b2cweapp-dev2021112700000085.qjclouds.com/web/rs/resourceGoods/getResourceGoodsInfoBySkuCode.json",
      code: "583978025764720650",
      goodsDetail: {},
      needSafe: false,
    };
  },
  mounted() {
    const that = this;
    that.needSafe = getApp().globalData.needSafe
    uni.request({
      url: "https://b2cweapp-dev2021112700000085.qjclouds.com/web/rs/resourceGoods/getResourceGoodsInfoBySkuCode.json",
      header: {
          "saas-Agent": "qj-wemini"
      },
      data: {
          skuCode: "583978025764720650"
      },
      success: function (res) {
          console.log(25, res?.data);
          that.goodsDetail = res?.data;
      }
    });
  },
  components: { 
    GdSwiper, 
    GdTitle, 
    GdPrice, 
    GdIntro, 
    GdFooter, 
    GdComment, 
    GdMarketingSize, 
    GdMarketingPromotion, 
    GdMarketingCoupon 
  }
}
</script>

<style scoped lang="less">
	.goodsDetail {
    padding-bottom: 5rem;
    .wrap {
      box-sizing: border-box;
      padding: 1.5rem;
    }
    .safe {
			width: 100%;
			height: 3rem;
		}
	}
</style>