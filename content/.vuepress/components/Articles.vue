<template>
  <div>
    <h2>Articles</h2>
    <ul>
      <li v-for="article in articles" :key="article.id">
        <a :href="article.link">{{article.title}}</a>
      </li>
    </ul>
  </div>
</template>

<script>
// import Vue from 'vue'

export default {
  data() {
    return {
      articles: []
    };
  },
  async mounted() {
    // this.articles = await Vue.rssParser.parseURL('https://medium.jasonmdesign.com/feed')
    // console.log(this.articles)
  }
};
</script>
