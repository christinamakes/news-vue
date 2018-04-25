<template>
  <v-container fluid grid-list-lg>
    <v-layout row wrap>
      <v-flex
      xs12
      sm6
      md4
      lg3
      v-for="(art, index) in articles"
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
</template>

<script>
export default {
  name: 'NewsCards',
  props: {
    articles: Array
  }
};
</script>
