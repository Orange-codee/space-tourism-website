<script setup>
import { RouterView } from 'vue-router';
import NavBar from './components/NavBar.vue';
</script>

<template>
  <header>
    <NavBar></NavBar>
  </header>

  <RouterView :key="$route.fullPath" />
</template>

<style></style>
