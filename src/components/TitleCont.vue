<template>
  <section class="cont__title">
    <div class="container">
      <h1>
        <strong>{{ name1 }}</strong>
        <em>{{ name2 }}</em>
      </h1>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    name1: String,
    name2: String,
  },
};
</script>

<style lang="scss">
// cont__title
.cont__title {
  padding: 15vmax 1% 10vmax;
  font-size: 5vmax;
  font-family: var(--main_font);
  text-transform: uppercase;
  line-height: 0.85;
  color: var(--white);

  em {
    display: block;
  }
}
.cont__title.light {
  background-color: var(--dark_bg);
  color: var(--black);
}
</style>
