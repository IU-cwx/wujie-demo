<template>
  <div class="app">
    <div class="main-app">main-app</div>

    <wuJie class="sub-app" url="//localhost:5174/" width="100%" height="100%" name="vue3" />
  </div>
</template>

<script setup lang="ts">
// import { ref } from "vue";
import wuJie from "wujie-vue3";
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: row;
  text-align: center;
  height: 100vh;
  padding: 4px;
}

.main-app {
  border: 1px solid blue;
  width: 200px;
  height: 100%;
  margin-right: 10px;
  padding: 10px;
}

.sub-app {
  border: 1px solid red;
  height: 100%;
  padding: 10px;
}
</style>
