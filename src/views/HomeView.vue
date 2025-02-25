<template>
  <main>
    <div class="homepage">
      <section>
        <span class="text-preset-5 blue-300">SO, YOU WANT TO TRAVEL TO</span>
        <span class="text-preset-1 white">SPACE</span>
        <span class="text-preset-9 blue-300"
          >Let’s face it; if you want to go to space, you might as well genuinely go to outer space
          and not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a
          truly out of this world experience!</span
        >
      </section>
      <button class="explore text-preset-4 blue-900" type="button" @click="goDestination">
        EXPLORE
      </button>
    </div>
  </main>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue';
import { useRouter } from 'vue-router';

// 背景圖片
onMounted(() => document.querySelector('body').classList.add('home-desktop-bg'));
onBeforeUnmount(() => document.querySelector('body').classList.remove('home-desktop-bg'));

const router = useRouter();
const goDestination = () => {
  router.push('/destination');
};
</script>

<style scoped lang="scss">
main {
  // border: 1px solid rgb(163, 165, 42);
  margin: 0 auto;
  padding: 128px 0px;
  div.homepage {
    border: 1px solid brown;
    display: flex;
    // flex-direction: row;
    justify-content: space-between;
    align-items: flex-end;
    height: 632px;
    // width: 1110px;
    max-width: 1110px;
    margin: 0 auto;
    section {
      display: flex;
      flex-direction: column;
      max-width: 540px;
      // border: 1px solid blue;
    }
    button.explore {
      height: 272px;
      width: 272px;
      border-radius: 50%;
      border: 0px;
      cursor: pointer;
      position: relative;
      transition: 0.4s ease-in-out;
      &::before {
        content: '';
        position: absolute;
        width: 360px;
        height: 360px;
        background: rgba(255, 255, 255, 0.1);
        border-radius: 50%;
        z-index: -1;
        transition:
          transform 0.4s ease-in-out,
          opacity 0.4s;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        opacity: 0;
      }
      &:hover::before {
        transform: translate(-50%, -50%);
        opacity: 1;
      }
    }
  }
}

@media screen and (max-width: 768px) {
  main {
    padding-left: 40px;
    padding-right: 40px;
    text-align: center;
    div.homepage {
      flex-direction: column;
      align-items: center;
    }
  }
}

@media screen and (max-width: 425px) {
  main {
    padding: 24px;
    div.homepage {
      section {
        span.text-preset-1 {
          margin: 24px 0;
        }
      }
      button.explore {
        height: 144px;
        width: 144px;
      }
    }
  }
}

@media screen and (max-width: 320px) {
  main {
    padding: 24px;
    div.homepage {
      button.explore::before {
        height: 300px;
        width: 300px;
      }
    }
  }
}
</style>
