<template>
  <header id="header">
    <div class="header__port">
      <a href="/port">portfolio</a>
    </div>
    <div class="header__logo">
      <a href="/">webdeveloper</a>
    </div>
    <div class="header__menu">
      <ul>
        <li>
          <a href="/about">About</a>
        </li>
        <li>
          <a href="/refer">Reference</a>
        </li>
        <li>
          <a href="/youtube">Youtube</a>
        </li>
        <li>
          <a href="/movie">Movie</a>
        </li>
        <li>
          <a href="/contact">Contact</a>
        </li>
      </ul>
    </div>
  </header>
</template>

<style lang="scss">
#header {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  color: var(--white);
  border-bottom: 1px solid var(--dark_border);
  background-color: var(--dark_bg);
  display: flex;
  align-items: center;
  font-family: "Rajdhani";
  z-index: 1000;
}
.header__port {
  flex: 1 1 40%;
  a {
    display: inline-block;
    padding: 1rem;
    text-transform: capitalize;
    position: relative;
    &::before {
      content: "";
      position: absolute;
      left: 1rem;
      bottom: 1rem;
      width: calc(100% - 2rem);
      height: 1px;
      background: var(--white);
      transform: scaleX(0);
      transition: all 0.3s ease;
    }
    &:hover::before {
      transform: scaleX(1);
    }
  }
}
.header__logo {
  flex: 1 1 20%;
  text-align: center;
  a {
    display: inline-block;
    font-size: 1.6rem;
    padding: 1rem;
  }
}
.header__menu {
  flex: 1 1 40%;
  text-align: right;
  li {
    display: inline;
    a {
      display: inline-block;
      padding: 1rem;
      position: relative;
      &::before {
        content: "";
        position: absolute;
        left: 1rem;
        bottom: 1rem;
        width: calc(100% - 2rem);
        height: 1px;
        background: var(--white);
        transform: scaleX(0);
        transition: all 0.3s ease;
      }
      &:hover::before {
        transform: scaleX(1);
      }
    }
  }
}
// 라이트 버전
.light#header {
  background-color: var(--light_bg);
  border-color: var(--light_border);
  a {
    color: var(--black);
    &::before {
      background: var(--black);
    }
  }
}
// 미디어 쿼리
@media (max-width: 1200px) {
  .header__menu {
    display: none;
  }
  .header__port {
    display: none;
  }
}

@media (max-width: 600px) {
  #header {
    background: rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(40px);
    border-bottom-color: #272727;
  }
  .light#header {
    background: var(--light_bg);
    backdrop-filter: blur(40px);
  }
}
</style>
