<template>
  <view class="GdComment">
    <view class="title">
      <text class="num">全部评价 (24)</text>
      <view class="all">
        <text class="txt">查看全部</text>
        <text class="iconfont icon-xiangyou"/>
      </view>
    </view>
    <view class="info">
      <view class="people">
        <image :src="logo" class="avatar"/>
        <text class="username">sdfdsfdsfdsf</text>
      </view>
    </view>
  </view>
</template>
<script>
import logo from "../../../static/logo.png"
export default {
  name: "GdComment",
  data() {
    return {
      logo
    }
  },
}
</script>
<style lang="less" scoped>
  .GdComment {
    border-top: 1rem solid #F8F8F8;
    border-bottom: 1rem solid #F8F8F8;
    box-sizing: border-box;
    padding: 2rem 1.5rem;
    .title {
      display: flex;
      justify-content: space-between;
      margin-bottom: 2.2rem;
      .num {
        font-size: 1.3rem;
        color: #333333;
      }
      .all {
        .txt {
          font-size: 1.3rem;
          color: #B79F77;
        }
        .iconfont {
          color: #B79F77;
          padding-left: 0.7rem;
        }
      }
    }
    .info {
      .people {
        .avatar {
          width: 2.4rem;
          height: 2.4rem;
          border-radius: 50%;
          margin-right: 1rem;
        }
        .username {
          vertical-align: top;
          display: inline-block;
          font-size: 1.2rem;
          color: #999999;
          height: 2.4rem;
          line-height: 2.4rem;
        }
      }
    }
  }
</style>