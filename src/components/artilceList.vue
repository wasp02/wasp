<script setup>
import { articles } from "../articles/test.js";
import { RouterLink } from "vue-router";
</script>

<template>
  <div class="article-list-wrapper">
    <div v-for="article in articles[0]">
      <router-link
        :to="{
          name: 'article',
          params: { id: article },
        }"
        ><p>{{ articles[1][article].name }}</p>
        <p id="article-list-paragraph">
          {{ articles[1][article].time }}
        </p></router-link
      >
    </div>
  </div>
</template>

<style>
@media (min-width: 443px) {
  .article-list-wrapper p {
    display: inline;
  }
}

.article-list-wrapper p:not(:last-child) {
  margin: 0 1rem 0 0;
}

.article-list-wrapper {
  max-width: 80vh;
  font-size: 1.5em;
  color: black;
  padding: 0 1em;
}

#article-list-paragraph {
  color: grey;
  font-size: 0.7em;
  vertical-align: text-bottom;
  margin: 0;
}

a:visited {
  color: black;
}
</style>
