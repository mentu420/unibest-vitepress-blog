<!-- 使用 type="home" 属性设置首页，其他页面不需要设置，默认为page；推荐使用json5，更强大，且允许注释 -->
<route lang="json5" type="home">
{
  style: {
    navigationStyle: 'custom',
    navigationBarTitleText: '首页',
  },
}
</route>
<template>
  <view
    class="bg-white overflow-hidden pt-2 px-4"
    :style="{ marginTop: safeAreaInsets?.top + 'px' }"
  >
    <view class="mt-12">
      <image src="/static/logo.svg" alt="" class="w-28 h-28 block mx-auto" />
    </view>
    <view class="text-center text-4xl main-title-color mt-4">unibest</view>
    <view class="text-center text-2xl mt-2 mb-8">最好用的 uniapp 开发模板</view>

    <view class="text-justify max-w-100 m-auto text-4 indent mb-2">{{ description }}</view>
    <view class="text-center mt-8">
      当前平台是：
      <text class="text-green-500">{{ PLATFORM.platform }}</text>
    </view>
    <view class="text-center mt-4">
      模板分支是：
      <text class="text-green-500">i18n</text>
    </view>
    <button class="btn">Button</button>
    <button class="btn btn-neutral">Neutral</button>
    <button class="btn btn-primary">Primary</button>
    <button class="btn btn-secondary">Secondary</button>
    <button class="btn btn-accent">Accent</button>
    <button class="btn btn-ghost">Ghost</button>
    <button class="btn btn-link">Link</button>
    <wd-button>主要按钮</wd-button>
    <wd-button type="success">成功按钮</wd-button>
    <wd-button type="info">信息按钮</wd-button>
    <wd-button type="warning">警告按钮</wd-button>
    <wd-button type="error">
      <span
        :class="
          [
            'i-mdi-thumb-up',
            'i-mdi-comment-processing',
            'i-mdi-share-all',
            'i-mdi-heart-multiple',
          ][3]
        "
      ></span>
    </wd-button>

    <wd-tabs v-model="tab">
      <block v-for="item in 4" :key="item">
        <wd-tab :title="`标签${item}`">
          <view class="content">内容{{ item }}</view>
        </wd-tab>
      </block>
    </wd-tabs>
    <wd-swiper
      :list="swiperList"
      autoplay
      :current="0"
      @click="handleClick"
      @change="onChange"
    ></wd-swiper>
  </view>
  <!-- <tabbar /> -->
</template>

<script lang="ts" setup>
import PLATFORM from '@/utils/platform'
import { getTaskList } from '@/apis/home'

defineOptions({
  name: 'Home',
})
const tab = ref<number>(0)
// 获取屏幕边界到安全区域距离
const { safeAreaInsets } = uni.getSystemInfoSync()
const author = ref('菲鸽')
const description = ref(
  'unibest 是一个集成了多种工具和技术的 uniapp 开发模板，由 uniapp + Vue3 + Ts + Vite4 + UnoCss + UniUI + VSCode 构建，模板具有代码提示、自动格式化、统一配置、代码片段等功能，并内置了许多常用的基本组件和基本功能，让你编写 uniapp 拥有 best 体验。',
)
const swiperList = ref([
  'https://unpkg.com/wot-design-uni-assets/redpanda.jpg',
  'https://unpkg.com/wot-design-uni-assets/capybara.jpg',
  'https://unpkg.com/wot-design-uni-assets/panda.jpg',
  'https://img.yzcdn.cn/vant/cat.jpeg',
  'https://unpkg.com/wot-design-uni-assets/meng.jpg',
])
function handleClick(e) {
  console.log(e)
}
function onChange(e) {
  console.log(e)
}

onLoad(() => {
  console.log(author)
})
</script>

<style>
.main-title-color {
  color: #d14328;
}
</style>
