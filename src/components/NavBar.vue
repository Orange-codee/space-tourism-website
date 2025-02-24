<template>
  <nav>
    <div>
      <img class="logo" src="@/assets/shared/logo.svg" alt="logo" />
      <span class="line"></span>
      <div class="links">
        <RouterLink class="text-preset-8 white" to="/"
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
      <a href="#"
        ><img class="ham-menu" src="@/assets/shared/icon-hamburger.svg" alt="ham-menu"
      /></a>
    </div>
  </nav>
</template>

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
      // flex: 1 0 auto;
      flex-shrink: 0;
      display: flex;
      flex-direction: row;
      justify-content: flex-end;
      align-items: center;
      // border: 1px solid red;
      background-color: rgb(255 255 255 / 0.05) /* #FFFFFF */;
      backdrop-filter: blur(80px);
      a {
        padding: 38.5px 0px;
        text-decoration: none;
        margin-left: 48px;
        // border: 1px solid green;
      }
    }
    a {
      img.ham-menu {
        display: none;
      }
    }
  }
}

a.active {
  // text-decoration: underline;
  // text-underline-offset: 38.5px;
  // text-decoration-thickness: 2px;
  border-bottom: solid 3px white;
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
        // flex-shrink: 1;
        // color: red;
        border: 1px solid yellow;
        // padding-right: 40px;
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
    }
  }
}
</style>
