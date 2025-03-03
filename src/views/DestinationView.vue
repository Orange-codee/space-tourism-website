<template>
  <main>
    <section>
      <h2 class="text-preset-5 white">
        <span class="bold chapter">01 </span>PICK YOUR DESTINATION
      </h2>
      <template v-for="(article, key) in articleContent" :key="key">
        <article v-if="currentContent === article.name">
          <img :src="imageSrc" :alt="article.name" />
          <div class="content">
            <div class="nav-tabs">
              <a
                class="text-preset-8 blue-300"
                :class="[currentContent === tab ? 'active' : '']"
                v-for="(tab, key) in navTabs"
                :key="key"
                href="#"
                @click.prevent="changeContent(tab)"
                >{{ tab }}
              </a>
            </div>
            <h1 class="text-preset-2 white">{{ article.name }}</h1>
            <p class="text-preset-9 blue-300">
              {{ article.description }}
            </p>
            <span class="line"></span>
            <div class="bot">
              <h3 class="text-preset-7 blue-300">
                AVG. DISTANCE <span class="text-preset-6 white">{{ article.distance }}</span>
              </h3>
              <h3 class="text-preset-7 blue-300">
                EST. TRAVEL TIME <span class="text-preset-6 white">{{ article.time }}</span>
              </h3>
            </div>
          </div>
        </article></template
      >
    </section>
  </main>
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

<style lang="scss" scoped>
main {
  padding: 48px 0;
  section {
    margin: 0 auto;
    min-height: 792px;
    max-width: 1110px;
    /* border: 1px solid rgb(25, 0, 255); */
    display: flex;
    flex-direction: column;
    h2 {
      margin-bottom: 24px;
      /* border: 1px solid white; */
    }
    article {
      flex: 1 1 auto;
      display: flex;
      justify-content: space-around;
      align-items: center;
      /* position: relative;
      top: 50%;
      transform: translateY(-50%); */
      /* border: 1px solid red; */
      img {
        width: 480px;
      }
      div.content {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        /* border: 1px solid yellow; */
        div.nav-tabs {
          display: flex;
          /* border: 1px solid blue; */
          margin-bottom: 40px;
          a {
            text-decoration: none;
            padding-bottom: 13px;
            margin-right: 32px;
            border-bottom: solid 3px transparent;
            transition: all 0.5s ease;
            &:hover {
              color: #ffffff;
              border-bottom: solid 3px white;
            }
            &.active {
              color: #ffffff;
              border-bottom: solid 3px white;
            }
          }
        }
        p {
          max-width: 445px;
        }
        span.line {
          margin: 40px 0;
          height: 1px;
          background-color: rgba(255, 255, 255, 0.25);
        }
        div.bot {
          display: flex;
          justify-content: flex-start;
          /* border: 1px solid yellowgreen; */
          h3 {
            flex-basis: 210.5px;
            margin-right: 24px;
            display: flex;
            flex-direction: column;
            span {
              margin-top: 12px;
            }
          }
        }
      }
    }
  }
}

@media screen and (max-width: 768px) {
  main {
    padding: 40px;
    /* border: 1px solid palegreen; */
    section {
      min-height: 848px;
      article {
        flex-direction: column;
        align-items: center;
        text-align: center;
        img {
          width: 300px;
          margin-bottom: 32px;
        }
        div.content {
          div.nav-tabs {
            justify-content: center;
            margin-bottom: 24px;
            a:first-of-type {
              margin-left: 32px;
            }
          }
          span.line {
            margin: 32px 0;
          }
        }
      }
    }
  }
}

@media screen and (max-width: 425px) {
  main {
    padding: 24px;
    section {
      height: auto;
      min-height: auto;
      display: flex;
      flex-direction: column;
      h2 {
        text-align: center;
      }
      article {
        position: static;
        transform: translateY(0);
        img {
          width: 150px;
        }
        div.content {
          div.bot {
            flex-direction: column;
            h3 {
              flex-basis: auto;
              margin-right: 0px;
              &:first-of-type {
                margin-bottom: 24px;
              }
            }
          }
        }
      }
    }
  }
}
</style>
