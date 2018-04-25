<template>
    <v-container fluid grid-list-lg>
      <v-layout row wrap>
        <v-flex
        xs12
        sm12
        md12
        lg12
        >
      <v-card>
        <v-card-title>{{overallSentiment}}, {{overallScore}}</v-card-title>
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