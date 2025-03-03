<template>
  <nav>
    <div>
      <img class="logo" src="@/assets/shared/logo.svg" alt="logo" />
      <span class="line"></span>
      <div class="links">
        <RouterLink style="margin-left: 48px" class="text-preset-8 white" to="/"
          ><span style="letter-spacing: 2.7px" class="bold hometag">00 </span
          ><span>HOME</span></RouterLink
        >
        <RouterLink class="text-preset-8 white" to="/destination"
          ><span style="letter-spacing: 2.7px" class="bold">01 </span><span>DESTINATION</span>
        </RouterLink>
        <RouterLink class="text-preset-8 white" to="/crew"
          ><span style="letter-spacing: 2.7px" class="bold">02 </span>CREW</RouterLink
        >
        <RouterLink class="text-preset-8 white" to="/technology"
          ><span style="letter-spacing: 2.7px" class="bold">03 </span>TECHNOLOGY</RouterLink
        >
      </div>
      <a href="#" @click.prevent="isOpen = !isOpen"
        ><img
          class="ham-menu"
          src="@/assets/shared/icon-hamburger.svg"
          alt="ham-menu"
          ref="hamMenu"
      /></a>
      <div class="mobile-menu" :class="{ active: isOpen }" ref="mobileMenu">
        <a class="ham-menu" href="#" @click.prevent="isOpen = !isOpen"
          ><img class="ham-menu" src="@/assets/shared/icon-close.svg" alt="ham-menu"
        /></a>

        <div class="mobilelinks">
          <RouterLink class="mobilelinks__item text-preset-8 white" to="/"
            ><span style="letter-spacing: 2.7px" class="bold hometag">00 </span
            ><span>HOME</span></RouterLink
          >
          <RouterLink class="mobilelinks__item text-preset-8 white" to="/destination"
            ><span style="letter-spacing: 2.7px" class="bold">01 </span><span>DESTINATION</span>
          </RouterLink>
          <RouterLink class="mobilelinks__item text-preset-8 white" to="/crew"
            ><span style="letter-spacing: 2.7px" class="bold">02 </span>CREW</RouterLink
          >
          <RouterLink class="mobilelinks__item text-preset-8 white" to="/technology"
            ><span style="letter-spacing: 2.7px" class="bold">03 </span>TECHNOLOGY</RouterLink
          >
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted, watch } from 'vue';
import { useRoute } from 'vue-router';
const route = useRoute();
const isOpen = ref(false);

//點擊外部關閉選單
const mobileMenu = ref(null);
const hamMenu = ref(null);

const handleClickOutside = (e) => {
  if (mobileMenu.value && !mobileMenu.value.contains(e.target) && e.target !== hamMenu.value) {
    isOpen.value = false;
  }
  // console.log(isOpen.value);
};

onMounted(() => {
  document.addEventListener('click', handleClickOutside);
});

onUnmounted(() => {
  document.removeEventListener('click', handleClickOutside);
});

//路由跳轉自動關閉選單
watch(route, () => {
  if (document.body.offsetWidth < 425) {
    isOpen.value = false;
  }
});
</script>

<style scoped lang="scss">
nav {
  padding-top: 40px;
  div {
    padding-left: 64px;
    padding-right: 64px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    // border: 1px solid yellow;
    img.logo {
      width: 48px;
      height: 48px;
      // border: 1px solid yellow;
    }
    span.line {
      flex: 1 1 560px;
      position: relative;
      z-index: 2;
      left: 4%;
      height: 1px;
      background-color: rgba(255, 255, 255, 0.25);
    }
    div.links {
      flex: 1 0 736px;
      display: flex;
      flex-direction: row;
      // justify-content: flex-end;
      align-items: center;
      // border: 1px solid red;
      background-color: rgb(255 255 255 / 0.05) /* #FFFFFF */;
      backdrop-filter: blur(80px);
      a {
        padding: 38.5px 0px;
        text-decoration: none;
        // margin-left: 48px;
        // border: 1px solid green;
        border-bottom: solid 3px transparent;
        transition: all 0.5s ease;
        &:hover {
          // text-decoration: underline;
          // text-underline-offset: 38.5px;
          // text-decoration-thickness: 2px;
          color: #ffffff;
          border-bottom: solid 3px white;
        }
        &.active {
          // text-decoration: underline;
          // text-underline-offset: 38.5px;
          // text-decoration-thickness: 2px;
          color: #ffffff;
          border-bottom: solid 3px white;
        }
      }
    }
    a {
      img.ham-menu {
        position: relative;
        display: none;
      }
    }
    div.mobile-menu {
      display: none;
    }
  }
}

@media screen and (max-width: 768px) {
  nav {
    padding-top: 0px;
    div {
      padding-left: 40px;
      padding-right: 0px;
      justify-content: space-between;
      span.line {
        display: none;
      }
      div.links {
        flex: 1 1 640px;
        // border: 1px solid yellow;
        padding-right: 40px;
      }
    }
  }

  .hometag {
    display: none;
  }

  a:first-of-type::before {
    display: none;
  }
}

@media screen and (max-width: 425px) {
  nav {
    padding: 24px;
    div {
      padding-left: 0px;
      div.links {
        display: none;
      }
      a {
        img.ham-menu {
          display: block;
        }
      }
      div.mobile-menu.active {
        display: flex;
        flex-direction: column;
        justify-content: start;
        padding-left: 32px;
        background-color: rgba(11, 13, 23, 0.15);
        backdrop-filter: blur(80px);
        width: 254px;
        height: 100vh;
        color: #ffffff;
        position: absolute;
        z-index: 3;
        top: 0px;
        right: 0px;
        a.ham-menu {
          margin: 32px 24px 32px auto;
          // border: 1px solid wheat;
          img {
            // border: 1px solid red;
          }
        }
        div.mobilelinks {
          margin-top: 48px;
          display: flex;
          flex-direction: column;
          align-items: flex-start;
          margin-right: auto;
          // border: 1px solid yellow;
          width: 100%;
          a.mobilelinks__item {
            text-decoration: none;
            margin-bottom: 32px;
            border-right: 3px solid transparent;
            width: 100%;
            &.active {
              border-right: 3px solid #ffffff;
            }
          }
        }
      }
    }
  }

  .hometag {
    display: unset;
  }
}
</style>
