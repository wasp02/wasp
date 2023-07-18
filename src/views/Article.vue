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

function getInterview() {
  return articles[1][props.id].interview;
}
</script>

<template>
  <div className="article-wrapper">
    <div className="paragraph-wrapper">
      <h1>{{ articles[1][props.id].name }}</h1>
      <time>{{ getTime() }}</time>
      <p v-for="para in getData()">{{ para }}</p>
      <p>{{ getInterview().interviewee }} -</p>
      <p>{{ getInterview().content }}</p>
    </div>
    <hr />
    <div className="dialog-wrapper">
      <p>Favourite dialog:</p>
      <div className="dialog-container" v-for="line in getLines()">
        <i>{{ line[0] }}</i>
        <p>{{ line[1] }}</p>
      </div>
    </div>
    <hr />
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

p:not(:nth-last-child(2)) {
  margin: 2em 0;
}

.dialog-contianer > i {
  text-transform: uppercase;
}

.paragraph-wrapper > p:last-child {
  font-style: italic;
  padding-left: 2em;
  font-weight: bold;
  margin: 0;
}

hr {
  opacity: 50%;
  margin: 3em 0;
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

.dialog-container {
  text-align: center;
}

.dialog-container > p {
  margin: 0;
}

.still-wrapper {
  padding-bottom: 3em;
}

.still-wrapper img {
  max-width: 100%;
}

img {
  vertical-align: text-top;
}

.article-wrapper {
  max-width: 50vw;
  margin: auto;
}

@media screen and (max-width: 1000px) {
  .article-wrapper {
    max-width: 70vw;
  }
}

@media screen and (max-width: 600px) {
  .article-wrapper {
    max-width: 90vw;
  }
}
</style>
