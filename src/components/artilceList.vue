<script setup>
import { articles } from "../articles/test.js";
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <div class="article-list-wrapper">
    <div v-for="article in articles[0]">
      <router-link
        :to="{
          name: 'article',
          params: { id: article },
        }"
        >{{ article
        }}<span id="article-list-span">
          - {{ articles[1][article].time }}</span
        ></router-link
      >
    </div>
  </div>
</template>

<style>
.article-list-wrapper {
  max-width: 80vh;
  font-size: 1.5em;
  color: black;
}

#article-list-span {
  color: grey;
  font-size: 0.7em;
}

div > a {
  color: rgb(224, 8, 16);
}

a:visited {
  color: black;
}
</style>
