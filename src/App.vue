<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/Header.vue';
import HomeView from './views/HomeView.vue'
</script>

<template>

   <div class="header">
    <Header />
  </div>
  <div class="content">
    <RouterView />
  </div>
  
</template>

<style scoped lang="scss">

.header {
  max-width: 100%;
  height: 15dvh;
}

.content {
  max-width: 100%;
  height: 85dvh;
  text-align: center;
}

body{
  margin:0px;
}

</style>
