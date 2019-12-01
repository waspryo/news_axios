<template>
  <div>
    <v-container>
      <v-flex xs12 pb-5>
        <h2>News</h2>
      </v-flex>
      <!-- News -->
      <v-flex xs12 sm6 offset-sm3 v-for="(article, index) in articles" :key="index">
        <v-card class="mx-auto" max-width="400">
          <img :src="article.urlToImage" width="100%" height="200px">
          <v-img
            class="white--text align-end"
            height="200px"
            src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
          >
            <v-card-title>Top 10 Australian beaches</v-card-title>
          </v-img>

          <v-card-subtitle class="pb-0">Number 10</v-card-subtitle>

          <v-card-text class="text--primary">
            <div>Whitehaven Beach</div>

            <div>Whitsunday Island, Whitsunday Islands</div>
          </v-card-text>

          <v-card-actions>
            <v-btn color="orange" text>Share</v-btn>

            <v-btn color="orange" text>Explore</v-btn>
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-container>
  </div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const { articles } = await app.$axios.$get(
      "https://newsapi.org/v2/everything?q=bitcoin&from=2019-11-01&sortBy=publishedAt&apiKey=ACCESS_TOKEN"
    );
    return (articles);
  }
};
</script>