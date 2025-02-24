<template>
  <div>
    <h1>Des</h1>
  </div>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue';

// 背景圖片
onMounted(() => document.querySelector('body').classList.add('des-desktop-bg'));
onBeforeUnmount(() => document.querySelector('body').classList.remove('des-desktop-bg'));
</script>

<style></style>
