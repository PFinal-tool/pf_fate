<template>
  <div class="flex flex-row h-lvh antialiased text-gray-800 w-lvw">
    <Navigation />
    <div class="flex flex-col text-white content">
      <div class="content_container mx-auto rounded-md bg-black text-white flex flex-col items-center">
        <div class="flex h-20 w-full rounded-full">
          <div class="h-20 w-20">1</div>
          <div class="h-20 w-full ">1-1</div>
        </div>
        <div class="h-20 w-20 bg-red-500 rounded-full">2</div>
        <div class="h-20 w-20 bg-red-500 rounded-full">3</div>
      </div>
      <date-picker :lang="langString" v-model:value="date" type="datetime" :show-time-panel="showTimePanel"
                   @close="handleRangeClose">
                   <template #footer>
                    <button class="mx-btn mx-btn-text" @click="toggleTimePanel">
                      {{ showTimePanel ? '选择日期' : '选择时间' }}
                    </button>
                  </template>
      </date-picker>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
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
  showTimePanel.value= true;
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
