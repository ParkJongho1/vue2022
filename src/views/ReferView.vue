<template>
  <HeaderCont name1="reference" name2="book" />
  <main id="main">
    <TitleCont name1="reference" name2="book" />
    <section class="refer__cont">
      <div class="container">
        <div class="refer__inner">
          <h2>CSS</h2>
          <ul class="refer__list">
            <li v-for="htmlRefer in refer" :key="htmlRefer.id">
              <a :href="htmlRefer.link" target="_blank">
                <span class="id">{{ htmlRefer.id }}</span>
                <span class="title">{{ htmlRefer.title }}</span>
                <span class="desc">{{ htmlRefer.desc }}</span>
                <span class="use">{{ htmlRefer.use }}</span>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </section>
    <ContactCont />
  </main>
  <FooterCont />
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import { ref } from "vue";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },
  setup() {
    const refer = ref([]);

    const refences = () => {
      var requestOptions = {
        method: "GET",
        redirect: "follow",
      };
      fetch(
        "https://parkjongho1.github.io/react2022/src/assets/json/reference.json",
        requestOptions
      )
        .then((response) => response.json())
        .then((data) => (refer.value = data.data.htmlRefer))
        .catch((error) => console.log("error", error));
    };

    refences();

    return {
      refer,
      refences,
    };
  },
};
</script>

<style lang="scss">
.refer__cont {
  background-color: var(--dark_bg);
  min-height: 100vh;
}
.refer__inner {
  h2 {
    color: var(--white);
    font-size: 2rem;
    margin-bottom: 1.6rem;
  }
  .img_table {
    display: flex;
    margin-bottom: 20px;
  }
  .img {
    overflow: hidden;
    width: 40%;
    margin-right: 20px;
    margin-top: 20px;
    border: 2px solid var(--light_bg);
    img {
      height: 100%;
    }
    .table {
      margin-top: 20px;
    }
  }
}

.refer__list {
  border-top: 2px solid var(--light_bg);
  border-bottom: 1px solid var(--light_bg);

  a {
    display: block;
    color: var(--white);
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid var(--light_bg);
    padding: 1.3rem 0;
    transition: all 0.3s;
    font-family: var(--subKor_font);

    &:hover {
      background: var(--light_bg);
      color: var(--black);
    }

    span {
      display: inline-block;
    }
    span:nth-child(1) {
      width: 6%;
      text-align: center;
    }
    span:nth-child(2) {
      width: 20%;
    }
    span:nth-child(3) {
      width: 64%;
    }
    span:nth-child(4) {
      width: 10%;
      text-align: center;
    }
  }
}

.refer__table {
  color: var(--white);
  font-family: var(--subKor_font);

  h3 {
    font-size: 3rem;
    margin-bottom: 1.3rem;
  }
  p {
    background: var(--light_bg);
    color: var(--black);
    padding: 1.4rem;
  }

  .table {
    color: var(--white);
    font-family: var(--subKor_font);
    border: 1px solid var(--light_bg);
    margin-top: 0.5em;

    th,
    td {
      font-weight: normal;
      padding: 1em;
      // border-bottom: 1px solid var(--light_bg);
      // border-left: 1px solid var(--light_bg);
      border: 1px solid var(--light_bg);
    }
  }
}
.table01 {
  padding-top: 200px;
}
.table02 {
  padding-bottom: 400px;
}

.img__table {
  display: flex;
  margin-bottom: 1.5rem;
  .refer__img {
    width: 50%;
    border: 2px solid var(--light_bg);
    margin: 1.5rem 1.5rem 0 0;
    overflow: hidden;
    img {
      width: 100%;
      height: 100%;
    }
  }
  .table {
    margin-top: 1.5rem;
  }
}

.refer__cont.light {
  background-color: var(--light_bg);
  .refer__inner {
    h2 {
      color: var(--black);
    }
    table {
      border-color: var(--black);
      color: var(--black);
      td {
        border-color: var(--black);
      }
    }
  }
}

@media (max-width: 1100px) {
  .refer__cont {
    margin: 0 auto;
    width: 100%;
  }
}
@media (max-width: 800px) {
  .img__table {
    flex-direction: column;
    .refer__img {
      width: 100%;
      max-height: 300px;
      overflow: hidden;
      display: flex;
      align-items: center;
    }
  }
}
</style>
