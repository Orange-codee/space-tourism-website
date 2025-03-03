<template>
  <main>
    <section>
      <h2 class="text-preset-5 white"><span class="bold chapter">02 </span>MEET YOUR CREW</h2>
      <article>
        <div class="content">
          <h1 class="text-preset-3 white">
            <span class="text-preset-4">{{ crews[currentIndex].role }}</span
            >{{ crews[currentIndex].name }}
          </h1>
          <p class="text-preset-9 blue-300">{{ crews[currentIndex].description }}</p>
          <div class="indicators">
            <button
              type="button"
              class="indicator"
              v-for="(crew, index) in crews"
              :key="index"
              @click="selectSlide(index)"
              :class="{ active: currentIndex === index }"
            ></button>
          </div>
        </div>
        <img :src="imageSrc" :alt="crews[currentIndex].name" />
      </article>
    </section>
  </main>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref, computed } from 'vue';

// 背景圖片
onMounted(() => document.querySelector('body').classList.add('crew-desktop-bg'));
onBeforeUnmount(() => document.querySelector('body').classList.remove('crew-desktop-bg'));

// 切換頁籤
const currentIndex = ref(0);
const selectSlide = (id) => (currentIndex.value = id);

const crews = ref([
  {
    role: 'COMMANDER',
    name: 'DOUGLAS HURLEY',
    description:
      'Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.',
  },
  {
    role: 'MISSION SPECIALIST',
    name: 'MARK SHUTTLEWORTH',
    description:
      'Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.',
  },
  {
    role: 'PILOT',
    name: 'VICTOR GLOVER',
    description:
      'Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.',
  },
  {
    role: 'FLIGHT ENGINEER',
    name: 'ANOUSHEH ANSARI',
    description:
      'Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.',
  },
]);
// 圖片路徑
const imageSrc = computed(() => {
  return new URL(
    `../assets/crew/image-${crews.value[currentIndex.value].name.toLowerCase().split(' ').join('-')}.png`,
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
    // border: 1px solid rgb(25, 0, 255);
    display: flex;
    flex-direction: column;
    h2 {
      margin-bottom: 24px;
    }
    article {
      flex: 1 1 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      // border: 1px solid yellow;
      div.content {
        display: flex;
        flex-direction: column;
        max-width: 539px;
        h1 {
          display: flex;
          flex-direction: column;
          span {
            margin-bottom: 16px;
            opacity: 0.5042;
          }
        }
        p {
          margin-top: 24px;
        }
        div.indicators {
          margin-top: 40px;
          button.indicator {
            margin-right: 40px;
            width: 15px;
            height: 15px;
            border-radius: 50%;
            border: none;
            background-color: #ffffff;
            opacity: 0.1744;
            cursor: pointer;
            transition: opacity 1s ease-out;
            &:hover {
              opacity: 1;
            }
            &.active {
              // 使用 &.active 確保優先級
              background-color: #ffffff;
              opacity: 1;
            }
          }
        }
      }
      img {
        // margin-left: 32px;
        width: 539.28px;
      }
    }
  }
}

@media screen and (max-width: 768px) {
  main {
    padding: 40px 40px 0 40px;
    section {
      min-height: 848px;
      article {
        flex-direction: column;
        text-align: center;
        div.content {
          margin-bottom: 32px;
          div.indicators {
            margin-top: 24px;
          }
        }
        img {
          width: 446.74px;
        }
      }
    }
  }
}

@media screen and (max-width: 425px) {
  main {
    padding: 24px;
    section {
      h2 {
        text-align: center;
      }
      article {
        div.content {
          div.indicators {
            button.indicator {
              width: 10px;
              height: 10px;
              margin-right: 16px;
              &:first-of-type {
                margin-right: 16px;
              }
            }
          }
        }
        img {
          width: 327px;
        }
      }
    }
  }
}
</style>
