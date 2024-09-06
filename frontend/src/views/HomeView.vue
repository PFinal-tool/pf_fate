<template>
  <div class="flex flex-row h-lvh antialiased text-gray-800 w-lvw">
    <!-- 导航栏 -->
    <Navigation />
    <div class="flex flex-col text-white content container">
      <!-- 内容容器 -->
      <div class="w-full h-40 grid grid-rows-4 grid-flow-col gap-4">
        <!-- 第一行，占四个格子，第一列 -->
        <div class="row-span-4 pt-11 col-span-1">
          <!-- 头像 -->
          <div class="h-20 w-20 rounded-md bg-green-400 float-end">
            <UserCircleIcon className="size-6 text-blue-500 rounded-full" />
          </div>
        </div>
        <!-- 第二行，最后一列，底部对齐 -->
        <div class="row-span-2 col-span-12 items-start flex flex-col">
          <p class="inline-block mt-11 h-full leading-snug">111</p>
        </div>

        <!-- 第三行，占两个格子，横跨所有列 -->
        <div class="row-span-2 col-span-12 bg-indigo-600">03</div>
      </div>
      <!-- 日期选择器 -->
      <div class="">
        <date-picker :lang="langString" v-model:value="date" type="datetime" :show-time-panel="showTimePanel"
                     @close="handleRangeClose">
          <!-- 自定义底部 -->
          <template #footer>
            <button class="mx-btn mx-btn-text" @click="toggleTimePanel">
              {{ showTimePanel ? '选择日期' : '选择时间' }}
            </button>
          </template>
        </date-picker>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import { UserCircleIcon } from '@heroicons/vue/24/solid'
import lunisolar from 'lunisolar'

import Navigation from "../components/Navigation.vue";
import DatePicker from 'vue-datepicker-next';
import 'vue-datepicker-next/index.css';
import 'vue-datepicker-next/locale/zh-cn';

const toDay = new Date(2024, 8, 6, 14, 30, 0)
const date = ref(toDay);
const langString = 'zh-cn'
const showTimePanel = ref(false)
const showTimeRangePanel = ref(false)
// 格式化日期
const formattedDate = ref(toDay.toLocaleString('zh-CN', {
  year: 'numeric',
  month: '2-digit',
  day: '2-digit',
  hour: '2-digit',
  minute: '2-digit',
  second: '2-digit',
  hour12: false
}));

const d = ref(lunisolar(formattedDate.value))
console.log(d.value.lunar.toString())

const handleOpenChange = () => {
  showTimePanel.value = true;
};

const handleRangeClose = () => {
  showTimePanel.value = false;
};

const toggleTimePanel = () => {
  showTimePanel.value = !showTimePanel.value;
};


// 监听 date 的变化
watch(date, (newDate, oldDate) => {
  console.log('日期改变了: 从', oldDate, '到', newDate);
  // 格式化  newDate 为 2023/09/06 14:30:00
  formattedDate.value = newDate.toLocaleString('zh-CN', {
    year: 'numeric',
    month: '2-digit',
    day: '2-digit',
    hour: '2-digit',
    minute: '2-digit',
    second: '2-digit',
    hour12: false
  });

  d.value = lunisolar(formattedDate.value)
  console.log(d.value.lunar.toString())
});




</script>

<style scoped>
.content {
  background-color: #2d2d2d;
}

.content_container {
  width: 94vw;
  height: 90vh;
  min-width: 5rem;
}
</style>
