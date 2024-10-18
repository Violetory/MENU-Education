<template>
  <view class="content">
    <Header />

    <!--TAB-->
    <view class="tab">
      <n-tabs
        type="segment"
        animated
        :model-value="currentTab"
        @click="changeTabs"
      >
        <n-tab-pane class="single-tab" name="chap1" tab="Recommend">
        </n-tab-pane>
        <n-tab-pane class="single-tab" name="chap2" tab="Free"> </n-tab-pane>
        <n-tab-pane class="single-tab" name="chap3" tab="Practice">
        </n-tab-pane>
      </n-tabs>
    </view>

    <!--COMPONENT SWIPER-->
    <!--<swiper class="component-swiper-container" @touchmove.stop>-->
    <!--  <swiper-item class="component-swiper-slide">Content1</swiper-item>-->
    <!--  <swiper-item class="component-swiper-slide">content2</swiper-item>-->
    <!--  <swiper-item class="component-swiper-slide">content3</swiper-item>-->
    <!--</swiper>-->

    <view class="component-swiper">
      <swiper class="component-swiper-container" @change="onSwiperChange">
        <swiper-item v-for="(item, index) in TabBar" :key="index">
          <view class="swiper-item">
            <component :is="item.component" />
          </view>
        </swiper-item>
      </swiper>
    </view>

    <!-- 外层 Swiper -->
    <!--<swiper class="component-swiper-container" @touchmove.stop>-->
    <!--  <swiper-item class="component-swiper-slide">-->
    <!--    &lt;!&ndash; 内层 Swiper &ndash;&gt;-->
    <!--    Content1-->
    <!--    <swiper class="swiper-container" :nested="true" @touchmove.stop.prevent="handleSwipe">-->
    <!--      <SwiperSlide class="swiper-slide">Slide1</SwiperSlide>&ndash;&gt;-->
    <!--      <SwiperSlide class="swiper-slide">Slide2</SwiperSlide>-->
    <!--      <SwiperSlide class="swiper-slide">Slide3</SwiperSlide>-->
    <!--    </swiper>-->
    <!--  </swiper-item>-->
    <!--  <swiper-item class="component-swiper-slide">Content 2</swiper-item>-->
    <!--  <swiper-item class="component-swiper-slide">Content 3</swiper-item>-->
    <!--</swiper>-->
  </view>
</template>

<script lang="ts" setup>
import { ref, shallowRef } from "vue";
import Header from "../../components/common/Header.vue";
import Recommend from "../../components/home/Recommend.vue";
import Free from "../../components/home/Free.vue";
import Practice from "../../components/home/Practice.vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectCards } from "swiper/modules";
import "swiper/css";
import "swiper/css/effect-cards";

/* TAB BAR DATA */
const TabBar = shallowRef([
  {
    name: "Recommend",
    component: Recommend,
  },
  {
    name: "Free",
    component: Free,
  },
  {
    name: "Practice",
    component: Practice,
  },
]);

/* INITIALIZE CURRENT TAB */
const currentTab = ref(0);

const changeTabs = (index) => {
  console.log("Tabs changed", index);
};

const onSwiperChange = (index) => {
  console.log("Swiper changed to", index);
};

const modules = ref([EffectCards]);

/* HANDLE SWIPE */
const handleSwipe = (event) => {
  event.stopPropagation();
};
</script>

<style>
/* CONTENT */
.content {
  position: relative;
  margin: 120rpx 5rpx 0 5rpx;

  .chat {
    align-items: center;
    width: 40rpx;
    height: 40rpx;
    margin-left: 15rpx;
  }

  /* TAB */
  .tab {
    margin: 15rpx 40rpx;
    background: none;
    border-radius: 30rpx;

    /deep/ .n-tabs-rail {
      padding: 0;
      background-color: white;

      /deep/ .n-tabs-capsule {
        border-radius: 50rpx;
      }
    }

    /deep/
      .n-tabs
      .n-tabs-rail
      .n-tabs-tab-wrapper
      .n-tabs-tab.n-tabs-tab--active {
      color: white;
    }

    /deep/ .n-tabs .n-tabs-rail .n-tabs-capsule {
      background-color: black;
    }
  }

  /* SWIPER */
  .swiper-container {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 610rpx;
    height: 400rpx;
    margin: 20rpx auto;

    .swiper-slide {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 300px;
      height: 200px;
      border-radius: 22px;
      font-size: 22px;
      font-weight: bold;
      color: #000;
    }

    .swiper-slide:nth-child(1n) {
      background-color: #f5f5f5;
    }

    .swiper-slide:nth-child(2n) {
      background-color: #d2d7f0;
    }

    .swiper-slide:nth-child(3n) {
      background-color: #9ee2b8;
    }
  }
}
</style>