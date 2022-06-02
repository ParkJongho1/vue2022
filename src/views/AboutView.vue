<template>
  <HeaderCont />
  <main id="main">
    <section class="about__cont">
      <TitleCont name1="introduce" name2="me" />
      <div class="container">
        <div class="about__inner">
          <div class="about" v-for="(item, index) in items" v-bind:key="index">
            <figure class="about__img">
              <img :src="item.img" :alt="item.title" />
            </figure>
            <div class="about__txt">
              <h3>{{ item.title }}</h3>
              <p>{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
      <ContactCont />
    </section>
  </main>
  <FooterCont />
</template>
<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";
export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },

  data: () => ({
    items: [
      {
        id: "1",
        title: "꿈을 설계하고 디자인하다.",
        desc: "운이 좋은 사람은 없다. 단지 운을 만들 뿐이다. 운을 만들기위해서는 내가 좋아하는 일이나 내가 하고 싶은 일에 몰두하면 된다.몰두 하다보면 길이 보이고 방향이 보이게 된다. 운이란 고된 노동과노력을 통해 스스로 만들어 내는 것이다. 복권에 당첨되는 사람들은금방 돈을 허비하게 된다. 단지 행운만 좋았기 때문이다. 운을 만든사람은 돈을 날려먹거나 헛되게 쓰지 않는다. 열심히 할수록 운은나에게 온다.",
        img: "img/coding.jpg",
      },
      {
        id: "2",
        title: "열심히 할수록 기회는 따른다.",
        desc: "운이 좋은 사람은 없다. 단지 운을 만들 뿐이다. 운을 만들기 위해서는 내가 좋아하는 일이나 내가 하고 싶은 일에 몰두하면 된다.몰두 하다보면 길이 보이고 방향이 보이게 된다. 운이란 고된 노동과 노력을 통해 스스로 만들어 내는 것이다.복권에 당첨되는 사람들은 금방 돈을 허비하게 된다. 단지 행운만 좋았기 때문이다. 운을 만든 사람은 돈을 날려먹거나 헛되게 쓰지 않는다.열심히 할수록 운은 나에게 온다.",
        img: "img/myphoto.jpg",
      },
      {
        id: "3",
        title: "나에게 정직하다.",
        desc: "나에게 정직하다. 정직은 다른 사람보다 나에게 큰 의미를 부여해야 한다. 자신이 정직하지 않으면 진정으로 원하는 일을 열정적으로 밀고 나갈 수 없다. 마음에서 우러나오는 일을 해야 정직해지며 삶을 더 즐길 줄 알게 된다. 다름 사람에게도 정직해야 하지만 그 무엇보다 나 자신한테 정직해야 한다.",
        img: "img/mywork.jpg",
      },
    ],
  }),
};
</script>
<style lang="scss" scoped>
.about__cont {
  background-color: var(--dark_bg);
}
.about__inner {
  .about {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding-bottom: 30vh;
    color: var(--white);
    font-family: var(--kor_font);
    h3 {
      margin-bottom: 30px;
      font-size: 1rem;
      line-height: 1;
    }
    p {
      font-size: 1rem;
      line-height: 1.6;
    }
    &:nth-child(1) {
      .about__img {
        flex: 0 0 100%;
      }
      .about__txt {
        flex: 0 0 100%;
        h3 {
          margin-top: 2rem;
        }
      }
    }
    &:nth-child(2) {
      .about__img {
        flex: 0 0 64%;
      }
      .about__txt {
        flex: 0 0 30%;
      }
    }
    &:nth-child(3) {
      flex-direction: row-reverse;
      .about__img {
        flex: 0 0 54%;
      }
      .about__txt {
        flex: 0 0 40%;
      }
    }
  }
}
.about__cont.light {
  background-color: var(--light_bg);
  .about {
    color: var(--black);
  }
}
@media (max-width: 1200px) {
  .about__cont {
    padding: 2%;
  }
}
@media (max-width: 960px) {
  .about__inner {
    .about {
      flex-direction: column;
      padding-bottom: 20vh;
      &:nth-child(3) {
        flex-direction: column;
      }
    }
    h3 {
      margin-top: 30px;
    }
  }
}
</style>
