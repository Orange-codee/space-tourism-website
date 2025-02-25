<template>
  <section>
    <h2 class="text-preset-5 white">
      <span style="letter-spacing: 4.72px" class="bold">01 </span>PICK YOUR DESTINATION
    </h2>
    <template v-for="(article, key) in articleContent" :key="key"
      ><article v-if="currentContent === article.name">
        <img :src="imageSrc" :alt="article.name" />
        <div class="nav-tabs" v-for="(tab, key) in navTabs" :key="key">
          <a class="text-preset-8 blue-300" href="#" @click.prevent="changeContent(tab)">{{
            tab
          }}</a>
        </div>
        <h1 class="text-preset-2 white">{{ article.name }}</h1>
        <p class="text-preset-9 blue-300">
          {{ article.description }}
        </p>
        <h3 class="text-preset-7 blue-300">
          AVG. DISTANCE <span class="text-preset-6 white">{{ article.distance }}</span>
        </h3>

        <h3 class="text-preset-7 blue-300">
          EST. TRAVEL TIME <span class="text-preset-6 white">{{ article.time }}</span>
        </h3>
      </article></template
    >
  </section>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref, computed } from 'vue';

// 背景圖片
onMounted(() => document.querySelector('body').classList.add('des-desktop-bg'));
onBeforeUnmount(() => document.querySelector('body').classList.remove('des-desktop-bg'));

// 切換頁籤
const navTabs = ref(['MOON', 'MARS', 'EUROPA', 'TITAN']);
const currentContent = ref('MOON');
const changeContent = (tab) => (currentContent.value = tab);

const articleContent = ref([
  {
    name: 'MOON',
    description:
      'See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.',
    distance: '384,400 KM',
    time: '3 DAYS',
  },
  {
    name: 'MARS',
    description:
      'Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!',
    distance: '225 MIL. KM',
    time: '9 MONTHS',
  },
  {
    name: 'EUROPA',
    description:
      'The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.',
    distance: '628 MIL. KM',
    time: '3 YEARS',
  },
  {
    name: 'TITAN',
    description:
      'The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.',
    distance: '1.6 BIL. KM',
    time: '7 YEARS',
  },
]);
// 圖片路徑
const imageSrc = computed(() => {
  return new URL(
    `../assets/destination/image-${currentContent.value.toLowerCase()}.png`,
    import.meta.url,
  ).href;
});
</script>

<style></style>
