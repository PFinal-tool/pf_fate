<template>
  <div class="flex flex-col items-center py-4 flex-shrink-0 bg-gray-700 h-full navbar">
    <a data-page="user_details"
       class="flex items-center justify-center h-12 w-12 bg-green-400 text-indigo-800 rounded-full mt-12">
      <h1 class="font-bold">F</h1>
    </a>
    <ul class="flex flex-col space-y-2 mt-12">
      <li>
        <a href="#" class="flex items-center lodePage" data-page="home" :class="isActive('/') ? 'bg-indigo-700' : ''"
           @click.prevent="navigate('/')">
          <span class="flex items-center justify-center text-indigo-100 hover:bg-indigo-700 h-12 w-12 rounded-2xl">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                 xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6">
              </path>
            </svg>
          </span>
        </a>
      </li>
      <li>
        <a href="#" class="flex items-center lodePage" :class="isActive('/about') ? 'bg-indigo-700' : ''"
           @click.prevent="navigate('/about')" data-page="about">
          <span class="flex items-center justify-center text-indigo-100 hover:bg-indigo-700 h-12 w-12 rounded-2xl">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                 stroke="currentColor" class="w-6 h-6">
              <path stroke-linecap="round" stroke-linejoin="round"
                    d="M14.25 9.75L16.5 12l-2.25 2.25m-4.5 0L7.5 12l2.25-2.25M6 20.25h12A2.25 2.25 0 0020.25 18V6A2.25 2.25 0 0018 3.75H6A2.25 2.25 0 003.75 6v12A2.25 2.25 0 006 20.25z" />
            </svg>
          </span>
        </a>
      </li>
      <!--           <li>
                       <a href="#" class="flex items-center lodePage" data="">
               <span class="flex items-center justify-center text-indigo-100 hover:bg-indigo-700 h-12 w-12 rounded-2xl">
                 <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                      xmlns="http://www.w3.org/2000/svg">
                   <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                         d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"></path>
                 </svg>
               </span>
                       </a>
                   </li> -->
      <li>
        <a href="#" class="flex items-center lodePage" data-page="setting">
          <span class="flex items-center justify-center text-indigo-100 hover:bg-indigo-700 h-12 w-12 rounded-2xl">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                 xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z">
              </path>
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path>
            </svg>
          </span>
        </a>
      </li>
    </ul>
    <button onclick="LoginOut()"
            class="mt-auto flex items-center justify-center hover:text-indigo-100 text-indigo-500 h-10 w-10">
      <span class="text-white text-xs">退 出</span>
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRoute, useRouter } from 'vue-router';

// 获取当前的 路由
const route = useRoute();
const router = useRouter(); // 请确保在你的应用中正确引入了 router 实例

console.log(route.path)

function isActive(path) {
  console.log(path)
  if (['/home', '/'].includes(route.path) && (path === '/home' || path === '/')) {
    return true;
  }
  // 对于其他路径，直接比较当前路径和期望路径是否相同
  return route.path === path;
}

// 导航到新路径
const navigate = (path) => {
  router.push(path);
}


</script>

<style scoped>
.navbar {
  min-width: 4rem;
  width: 4vw;
}
</style>