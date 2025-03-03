<template>
  <main>
    <section>
      <h2 class="text-preset-5 white"><span class="bold chapter">03 </span>SPACE LAUNCH 101</h2>
      <article>
        <div class="indicators">
          <button
            type="button"
            class="indicator text-preset-4 blue-900"
            v-for="(tech, index) in techs"
            :key="index"
            @click="selectSlide(index)"
            :class="{ active: currentIndex === index }"
          >
            {{ index + 1 }}
          </button>
        </div>
        <div class="paragragh">
          <h1 class="text-preset-3 white">
            <span class="text-preset-4">THE TERMINOLOGY...</span>{{ techs[currentIndex].name }}
          </h1>
          <p class="text-preset-9 blue-300">{{ techs[currentIndex].description }}</p>
        </div>
        <img :src="imageSrc" :alt="techs[currentIndex].name" />
      </article>
    </section>
  </main>
</template>

<script setup>
import { onMounted, onUnmounted, onBeforeUnmount, ref, computed } from 'vue';

// 背景圖片
onMounted(() => document.querySelector('body').classList.add('tech-desktop-bg'));
onBeforeUnmount(() => document.querySelector('body').classList.remove('tech-desktop-bg'));

//切換頁籤
const currentIndex = ref(0);
const selectSlide = (id) => (currentIndex.value = id);

const techs = ref([
  {
    name: 'LAUNCH VEHICLE',
    description:
      "A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a payload from Earth's surface to space, usually to Earth orbit or beyond. Our WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall, it's quite an awe-inspiring sight on the launch pad!",
  },
  {
    name: 'SPACEPORT',
    description:
      'A spaceport or cosmodrome is a site for launching (or receiving) spacecraft, by analogy to the seaport for ships or airport for aircraft. Based in the famous Cape Canaveral, our spaceport is ideally situated to take advantage of the Earth’s rotation for launch.',
  },
  {
    name: 'SPACE CAPSULE',
    description:
      "A space capsule is an often-crewed spacecraft that uses a blunt-body reentry capsule to reenter the Earth's atmosphere without wings. Our capsule is where you'll spend your time during the flight. It includes a space gym, cinema, and plenty of other activities to keep you entertained.",
  },
]);
// 圖片路徑
const isMobile = ref(window.innerWidth <= 768);
// 視窗大小變化
const updateScreenSize = () => {
  isMobile.value = window.innerWidth <= 768;
};
onMounted(() => {
  window.addEventListener('resize', updateScreenSize);
});
onUnmounted(() => {
  window.removeEventListener('resize', updateScreenSize);
});
const imageSrc = computed(() => {
  const imgType = isMobile.value ? 'landscape' : 'portrait';
  return new URL(
    `../assets/technology/image-${techs.value[currentIndex.value].name.toLowerCase().split(' ').join('-')}-${imgType}.jpg`,
    import.meta.url,
  ).href;
});
</script>

<style lang="scss" scoped>
main {
  padding: 48px 0;
  section {
    min-height: 792px;
    max-width: 1275px;
    display: flex;
    flex-direction: column;
    // border: 1px solid rgb(25, 0, 255);
    margin-left: auto;
    h2 {
      margin-bottom: 24px;
    }
    article {
      flex: 1 1 auto;
      display: flex;
      justify-content: end;
      align-items: center;
      // border: 1px solid yellow;
      div.indicators {
        display: flex;
        flex-direction: column;
        margin-right: 64px;
        button.indicator {
          width: 80px;
          height: 80px;
          border-radius: 50%;
          margin-bottom: 32px;
          border: 1px solid rgba(255, 255, 255, 0.25);
          background-color: transparent;
          color: #ffffff;
          cursor: pointer;
          transition: all 1s ease;
          &:hover {
            border: 1px solid rgba(255, 255, 255, 1);
          }
          &.active {
            background-color: #ffffff;
            color: #0b0d17;
          }
        }
      }
      div.paragragh {
        max-width: 491px;
        margin-right: 32px;
        h1 {
          display: flex;
          flex-direction: column;
          margin-bottom: 24px;
          span {
            opacity: 0.5042;
            margin-bottom: 16px;
          }
        }
      }
      img {
        width: 608px;
      }
    }
  }
}

@media screen and (max-width: 768px) {
  main {
    padding: 40px 0;
    section {
      min-height: auto;
      article {
        flex-direction: column;
        justify-content: center;
        // border: 1px solid blue;
        div.indicators {
          flex-direction: row;
          margin-right: 0px;
          margin-bottom: 40px;
          // border: 1px solid yellow;
          button.indicator {
            width: 56px;
            height: 56px;
            margin-right: 16px;
            margin-bottom: 0px;
            &:first-of-type {
              margin-left: 16px;
            }
          }
        }
        div.paragragh {
          text-align: center;
          margin-right: 0px;
          h1 {
            margin-bottom: 16px;
            // border: 1px solid green;
          }
        }
        img {
          order: -1;
          // width: 768px;
          width: 100vw;
          height: auto;
          display: block;
          margin-bottom: 32px;
          margin-top: 64px;
        }
      }
    }
  }
}

@media screen and (max-width: 425px) {
  main {
    padding: 24px 24px 48px 24px;
    section {
      h2 {
        text-align: center;
      }
      article {
        div.indicators {
          button.indicator {
            width: 40px;
            height: 40px;
          }
        }
        img {
          // max-width: 425px;
          // min-height: 258px;
          width: 100vw;
          height: auto;
          display: block;
        }
      }
    }
  }
}
</style>
