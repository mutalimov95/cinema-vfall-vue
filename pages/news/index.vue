<template>
  <main class="v-fall-main v-fall-main--page-news">
    <div class="v-fall__container v-fall__container--white v-fall__container--main">
      <section class="v-fall-main-block grid grid-column">
        <h2 class="v-fall-main-block__header">Новости</h2>
        <div class="v-fall-main-block__container grid grid-wrap">
          <a
            href="#"
            @click.prevent="openNews(item.url)"
            v-for="item of news"
            :key="item.id"
            class="v-fall-main-block__item v-fall-main-block__item--lg"
          >
            <img class="v-fall-main-block__img" :src="item.image" alt />
            <p
              class="v-fall-main-block__text"
            >{{item.title}}</p>
          </a>
        </div>
        <button class="v-fall-main-block__btn btn btn-disabled" type="button">Загрузить еще</button>
      </section>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      news: null
    }
  },
  mounted() {
    this.$axios.$get('https://api.videout.ru/news').then(response => (
      this.news = response.data
    ));
  },
  methods: {
    openNews(i) {
      this.$router.push(i)
    }
  }
};
</script>