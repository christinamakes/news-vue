<template>
  <v-app>
  <v-toolbar app>
    <v-toolbar-title>Search the News</v-toolbar-title>
  </v-toolbar>

  <main>
  <v-content>
    <v-container fluid>
      <router-view></router-view>

  <input name='message' v-model="message" value='message' placeholder="edit me">
  <p>Message is: {{ message }}</p>
    <v-tooltip top>
      <span slot='activator'>{{overallScore}}</span>
      <span>Overall score</span>
    </v-tooltip>
    <h1>{{overallSentiment}}</h1>
    
  <!-- TODO: CHANGE FROM MOCK CALL!! -->
  <!-- <button v-on:click="fetchNews(message)">Fetch</button> -->
  <button v-on:click="MOCKfetchNews()">Fetch</button>

<v-container fluid grid-list-md>
  <!-- TODO: CHANGE FROM MOCKDATA!! -->
  <v-layout row wrap>
    <v-flex
    xs12
    md6
    lg3
    v-for="(art, index) in mockData"
    :key='index'
    >
    <v-card :href="art.url" target='_blank' hover>
      <v-card-title primary-title>{{ art.title }}</v-card-title>
      <v-card-media
        :src="art.urlToImage || 'http://via.placeholder.com/200x200/f3h8e4/f3h8e4'"
        height="200px"
      >
      </v-card-media>
      <v-card-text>{{ art.description }}</v-card-text>
    </v-card>
    </v-flex>
  </v-layout>
</v-container>

    </v-container>
  </v-content>
  </main>
</v-app>
</template>

<script>
import mockData from '../assets/MOCK_DATA.json';
import axios from 'axios';

export default {
  name: 'HelloWorld',
  data() {
    return {
      message: '',
      isArticles: false,
      articles: [],
      overallScore: 0,
      overallSentiment: 0,
      mostNegative: '',
      mostPositive: '',
      mockData: [...mockData]
    };
  },
  computed: {},
  methods: {
    MOCKfetchNews() {
      this.overallScore = 61;
      this.overallSentiment = this.overallScore / 30;
      console.log(this.overallScore);
    },

    getNews: input => {
      return axios.get(
        'https://newsapi.org/v2/everything?apiKey=cffd5c18704145eb89a7156717753b11',
        {
          params: {
            // apiKey: 'cffd5c18704145eb89a7156717753b11',
            q: `+"${input}"-APKMirror`,
            from: '2018-4-15',
            language: 'en',
            sortBy: 'relevancy',
            sources:
              'bbc-news, abc-news, business-insider, cbs-news, cnbc, cnn, engadget, financial-times, fox-news, nbc-news, the-huffington-post, the-new-york-times, the-wall-street-journal, the-washington-post, usa-today, wired, time, the-economist, the-american-conservative',
            // REMOVE PAGE
            pageSize: 5
            // country: 'us',
          }
        }
      );
    },

    // PASS IN URL
    getEmotion(url) {
      return axios.get('https://api.dandelion.eu/datatxt/sent/v1', {
        dataType: 'json',
        params: {
          token: 'b97f5af544e14020b0887beef8e4a577',
          url: url
        }
      });
    },
    fetchNews(input) {
      this.getNews(input).then(res => {
        res.data.articles.map(article => this.articles.push(article));
        this.isArticles = true;
        console.log(this.isArticles);
        console.log(this.articles);
        let urls = [...res.data.articles.map(article => article.url)];

        urls.map(url => {
          this.getEmotion(url)
            .then(res => {
              this.overallScore += res.data.sentiment.score;
              console.log(res.data.url);
              console.log(res.data.sentiment.score);
            })
            .then(() => {
              this.overallSentiment = this.overallScore / 5;
            });
        });
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
