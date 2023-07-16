<script setup>
import { articles } from "../articles/test.js";

let props = defineProps({
  id: String,
});

function getData() {
  return articles[1][props.id].content;
}

function getTime() {
  return articles[1][props.id].time;
}

function getStill() {
  return "/wasp/" + articles[1][props.id].still;
}

function getLines() {
  return articles[1][props.id].lines;
}
</script>

<template>
  <div className="article-wrapper">
    <div className="paragraph-wrapper">
      <h1>{{ articles[1][props.id].name }}</h1>
      <time>{{ getTime() }}</time>
      <p v-for="para in getData()">{{ para }}</p>
    </div>
    <div className="dialog-wrapper">
      <p>Favourite dialog:</p>
      <div className="dialog-container" v-for="line in getLines()">
        <i>{{ line[0] }}</i>
        <p>{{ line[1] }}</p>
      </div>
    </div>
    <div className="still-wrapper">
      <p>Favourite still:</p>
      <img :src="getStill()" />
    </div>
  </div>
</template>

<style>
time {
  margin-top: 2em;
}

pre {
  white-space: pre;
}

i {
  text-transform: uppercase;
}

.dialog-wrapper {
  margin-bottom: 4em;
}

.dialog-wrapper > p {
  font-weight: bold;
}

.still-wrapper > p {
  font-weight: bold;
}

.dialog-wrapper .dialog-container:not(:last-child) {
  margin-bottom: 2em;
}

.paragraph-wrapper > p:not(:last-child) {
  margin-bottom: 2em;
}

.paragraph-wrapper {
  margin-bottom: 4em;
}

.dialog-container {
  text-align: center;
}

.dialog-container > p {
  margin: 0;
}

.still-wrapper {
  max-width: inherit;
}

.still-wrapper img {
  max-width: inherit;
}

img {
  vertical-align: text-top;
}

.article-wrapper {
  max-width: 90vh;
  margin: auto;
}
</style>
