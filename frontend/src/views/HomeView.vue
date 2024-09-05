<template>
  <div class="flex flex-row h-lvh antialiased text-gray-800 w-lvw">
    <Navigation />
    <div class="flex flex-col text-white bg-gray-800" >
      <div class="content_container mx-auto rounded-md border-gray-400 bg-yellow-50">
        sss
      </div>
    </div>
  </div>
</template>

<script setup>
import Navigation  from "../components/Navigation.vue";
</script>

<style scoped>
.content_container {
  width: 94vw;
  height: 90vh;
  min-width: 5rem;
}
</style>
