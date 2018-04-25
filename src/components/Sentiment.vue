<template>
    <v-container fluid grid-list-lg>
    <v-layout row wrap>
      <v-flex
      xs12
      sm6
      md4
      lg3
      >
      <v-card>
        <v-card-title>{{overallSentiment}}, {{overallScore}} This is the title card</v-card-title>
        <v-card-media src="https://images.pexels.com/photos/104827/cat-pet-animal-domestic-104827.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260" height="200px"></v-card-media>
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
    overallScore: Number
  }
};
</script>