<template>
  <v-app>
    {{overallSentiment}}
  </v-app>
</template>

<script>
export default {
  name: 'Sentiment',
  props: {
    overallSentiment: 0
  },
  data: {}
};
</script>