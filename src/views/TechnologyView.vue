<template>Tech</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue';

// 背景圖片
onMounted(() => document.querySelector('body').classList.add('tech-desktop-bg'));
onBeforeUnmount(() => document.querySelector('body').classList.remove('tech-desktop-bg'));
</script>
