<template>
    <v-container fluid grid-list-lg>
    <v-layout row wrap justify-center>
        <v-flex xs12 s12 md4 lg4>
          <v-card dark color="red">
            <v-card-title>Overall score</v-card-title>
            <v-card-text>{{ overallScore }}</v-card-text>
          </v-card>
        </v-flex>
        <v-flex xs12 s12 md4 lg4>
          <v-card>
            <v-card-text>The sentiment score of the most positive article was: <span class='green-txt'>{{ mostPositive }}</span></v-card-text>
            <v-card-text>The sentiment score of the most negative article was: <span class='red-txt'>{{ mostNegative }}</span></v-card-text>
          </v-card>
        </v-flex>
        <v-flex xs12 s12 md4 lg4>
          <v-card height="250px" dark :color="moodColor">
            <v-card-title>Overall mood for {{ search }} in the news:</v-card-title>
            <v-card-media :src="mood" height="170px" contain></v-card-media>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>  
</template>

<script>
export default {
  name: 'Sentiment',
  props: {
    overallSentiment: Number,
    overallScore: Number,
    mood: String,
    moodColor: String,
    search: String,
    mostPositive: Number,
    mostNegative: Number
  }
};
</script>

<style scoped>
.green-txt {
  font-weight: bold;
  color: #4caf50;
}

.red-txt {
  font-weight: bold;
  color: #f44336;
}
</style>
