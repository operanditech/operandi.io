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
import htmlparser from 'htmlparser2'

export default {
  data() {
    return {
      articles: []
    };
  },
  async mounted() {
    var response = await fetch('https://cors-anywhere.herokuapp.com/https://medium.jasonmdesign.com/rss');
    var dom = htmlparser.parseDOM(await response.text());

    this.articles = dom.find((elem) => elem.name == 'rss')
      .children.find((elem) => elem.name == 'channel')
      .children.find((elem) => elem.name == 'atom:link')
      .children.find((elem) => elem.name == 'atom:link')
      .children.filter((elem) => elem.name == 'item')
      .map((elem, index) => {
        return {
          title: elem.children.find((e) => e.name == 'title').children[0].data.replace("[CDATA[", "").replace("]]", ""),
          link: elem.children.find((e) => e.name == 'link').next.data,
          id: elem.children.find((e) => e.name == 'guid').children[0].data
        };
      });
  }
};
</script>
