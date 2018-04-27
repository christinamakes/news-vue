<template>
    <v-container fluid grid-list-lg>
    <v-layout row wrap justify-center>
        <v-flex xs12 s12 md2 lg2>
          <v-card height="250px" dark color="purple">
            <v-card-title class="justify-center"><span class="headline">Overall sentiment</span></v-card-title>
            <v-card-text class="text-xs-center"><span class="green-txt">{{ overallSentiment.toFixed(2) }}</span></v-card-text>
          </v-card>
        </v-flex>

        <v-flex xs12 s12 md3 lg3>
          <v-card dark height="250px" :color="moodColor">
            <v-card-title><span class="headline">Overall mood for {{ search }}:</span></v-card-title>
            <v-card-media :src="mood" height="170px" contain></v-card-media>
          </v-card>
        </v-flex>

        <v-flex xs12 s12 md2 lg2>
          <v-card dark height="250px" color="teal">
            <v-card-title class="justify-center"><span class="headline">Most Positive</span></v-card-title>
            <v-card-text class="text-xs-center"><span class="green-txt">{{ mostPositive }}</span></span></v-card-text>
          </v-card>
        </v-flex>
        
      
        <v-flex xs12 s12 md2 lg2>
          <v-card dark height="250px" color="pink darken-1">
            <v-card-title class="justify-center"><span class="headline">Most Negative</span></v-card-title>
            <v-card-text class="text-xs-center"><span class='red-txt'>{{ mostNegative }}</span></v-card-text>
          </v-card>
        </v-flex>

        <v-flex xs12 s12 md3 lg3>
          <v-card dark height="250px" color="orange darken-1">
            <v-card-title class="justify-center"><span class="headline">Artilces analyzed</span></v-card-title>
            <v-card-text class="text-xs-center"><span class='red-txt'>{{ articleNumber }}</span></v-card-text>
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
    mostNegative: Number,
    articleNumber: Number
  }
};
</script>

<style scoped>
.green-txt {
  font-weight: bold;
  font-size: 3em;
}

.red-txt {
  font-weight: bold;
  font-size: 3em;
}
</style>
