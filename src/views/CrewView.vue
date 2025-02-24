<template>Crew</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue';

// 背景圖片
onMounted(() => document.querySelector('body').classList.add('crew-desktop-bg'));
onBeforeUnmount(() => document.querySelector('body').classList.remove('crew-desktop-bg'));
</script>
