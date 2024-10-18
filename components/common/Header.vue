<template>
  <view class="content">
    <!--HEADER SEARCH-->
    <!--<van-search v-model="value" shape="round" class="vant-search" />-->
    <view class="header-search">
      <view class="header-search-main">
        <img
          alt="search-icon"
          class="search-icon"
          referrerpolicy="no-referrer"
          src="https://lanhu-oss.lanhuapp.com/FigmaDDSSlicePNG7c679e922bb0e925338b25532a16b343.png"
        />
      </view>
      <view class="chat-icon">
        <img
          alt="chat-icon"
          class="label_2"
          referrerpolicy="no-referrer"
          src="https://lanhu-oss.lanhuapp.com/FigmaDDSSlicePNG829afc409ee34527795e3fd8cfe58e46.png"
        />
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup></script>

<style>
/* HEADER SEARCH */
.header-search {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 30rpx;

  .header-search-main {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 70rpx;
    background: #f5f5f5;
    border-radius: 50rpx;
  }

  .search-icon {
    width: 40rpx;
    height: 40rpx;
    margin: 15rpx 20rpx;
  }

  .chat-icon {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 50rpx;
    height: 50rpx;
    margin: 0 25rpx;
  }
}
</style>