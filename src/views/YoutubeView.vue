<template>
  <HeaderCont />
  <main id="main">
    <TitleCont name1="youtube" name2="book" />
    <section class="youtube__cont">
      <div class="container">
        <div class="youtube__inner">
          <div class="youtube__search container">
            <form @submit.prevent="SearchYoutube()">
              <div>
                <label for="" class="ir_so">검색하기</label>
                <button type="submit">검색</button>
                <input
                  type="search"
                  id="search"
                  placeholder="검색하기"
                  v-model="search"
                />
              </div>
            </form>
          </div>
          <div class="youtube__list">
            <ul>
              <li v-for="youtube in youtubes" :key="youtube.id.videoId">
                <a href="" target="_blank" rel="noreferrer">
                  <img
                    :src="youtube.snippet.thumbnails.medium.url"
                    :alt="youtube.snippet.title"
                  />
                  <p>{{ youtube.snippet.title }}</p>
                </a>
              </li>
            </ul>
          </div>
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
    const youtubes = ref("");
    const search = ref("webstoryboy");
    const SearchYoutube = () => {
      var requestOptions = {
        method: "GET",
        redirect: "follow",
      };
      fetch(
        `https://youtube.googleapis.com/youtube/v3/search?part=snippet&maxResults=28&q=${search.value}&key=AIzaSyBEEA07JBuc07ddSmLxwpbIKdKmcWxruWA&type=video`,
        requestOptions
      )
        .then((response) => response.json())
        .then((data) => {
          youtubes.value = data.items;
          search.value = "";
          console.log(youtubes);
        })
        .catch((error) => console.log("error", error));
    };

    SearchYoutube();

    return {
      youtubes,
      search,
      SearchYoutube,
    };
  },
};
</script>

<style lang="scss">
.youtube__cont {
  background-color: var(--dark_bg);
}
.youtube__inner {
}

.youtube__list {
  ul {
    display: flex;
    flex-wrap: wrap;
    li {
      flex: 1 1 23%;
      margin: 1%;
      img {
        border-radius: 0.4em;
      }
      p {
        color: var(--white);
        font-family: var(--subKor_font);
        padding-top: 10px;
      }
    }
  }
}

.youtube__search {
  position: relative;
  h2 {
    color: var(--white);
    font-size: 40px;
    font-family: var(--subKor_font);
    text-indent: -9999px;
    width: 0;
    height: 0;
  }
  input {
    border: 2px solid var(--light_border);
    width: 98%;
    background: var(--black);
    border-radius: 50px;
    padding: 1rem 5rem 1rem 2rem;
    color: var(--light_bg);
    font-family: var(--subKor_font);
    margin: 0 1%;
    margin-bottom: 5%;
  }
  button {
    position: absolute;
    right: 20px;
    top: 9px;
    background: transparent;
    border: 0;
    color: var(--black);
    background: var(--white);
    font-family: var(--subKor_font);
    width: 40px;
    height: 40px;
    border-radius: 50%;
    font-size: 12px;
    transition: opacity 0.3 ease;

    &:active {
      opacity: 0.7;
    }
  }
}

@media (max-width: 1000px) {
  .youtube__list ul li {
    flex: 1 1 43%;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
  }
}

@media (max-width: 600px) {
  .youtube__list ul li {
    flex: 1 1 96%;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
  }
}
</style>
