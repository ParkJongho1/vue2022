<template>
  <main id="main">
    <section class="cont__contact">
      <p>Let’s create something new</p>
      <h3>LET`S GET IN <em>TOUCH</em></h3>
      <a href="/">contact me</a>
    </section>
  </main>
</template>

<style lang="scss">
.contact__cont {
  background-color: var(--dark_bg);
  height: 100vh;
}
.contact__inner {
  color: var(--white);
  align-content: center;
  justify-content: center;
  display: flex;
  flex-wrap: wrap;
  height: 100vh;

  .text {
    font-size: 9vw;
    line-height: 0.85;
    font-family: var(--main_font);
    text-transform: uppercase;
    width: 100%;

    div:nth-child(2) {
      text-align: center;
      padding-right: 13vw;
    }

    div:nth-child(3) {
      text-align: right;
    }
  }
  .desc {
    margin-left: 70%;
    text-align: left;
    font-size: 1rem;
    font-family: var(--kor_font);
    line-height: 1.5;
    padding-top: 2rem;
  }
}

@media (max-width: 1200px) {
  .contact__inner {
    .text {
      div {
        text-align: center;
      }
      div:nth-child(2) {
        text-align: center;
        padding-right: 0;
      }
      div:nth-child(3) {
        text-align: center;
      }
    }
    .desc {
      margin-left: 0;
      width: 40vw;
      text-align: center;
      word-break: keep-all;
    }
  }
}

@media (max-width: 600px) {
  .contact__inner {
    .text {
      font-size: 60px;
    }
    .desc {
      width: 90vw;
    }
  }
}
</style>
