<script setup lang="ts">
import { ref } from 'vue';

const url = ref('https://vuejs.org/');

const isDisabled = ref(true);

const widthOrHeight = ref("width");
const widthOrHeightValue = ref(100);

const imageAttributes = ref({
  src: "https://vuejs.org/images/logo.png",
  alt: "Vue.js",
  width: 100,
  height: 100
})

const style = ref({
  color: "red",
  fontSize: "20px"
})

const randValue = ref('まだです');
const onButtonClick = ():void => {
  const rand = Math.round(Math.random() * 10);
  randValue.value = rand.toString();
}
</script>

<template>
  <p><a v-bind:href="url" target="_blank">Vue.js</a></p>

  <p><a :href="url" target="_blank">Vue.js(省略形)</a></p>

  <p><a v-bind:href="url + 'guide/introduction.html'" target="_blank">Vue.js(ガイドページ)</a></p>

  <p><button v-bind:disabled="isDisabled">ボタン</button></p>

  <p><img v-bind:[widthOrHeight]="widthOrHeightValue" src="https://vuejs.org/images/logo.png" alt="Vue.js"></p>

  <p><img v-bind="imageAttributes"></p>

  <p><span :style="{ color: 'blue', fontSize: '20px' }">Vue.js(省略形)</span></p>

  <p><span v-bind:style="style">Vue.js</span></p>


  <button v-on:click="onButtonClick">ボタン</button>
  <p>ランダムな値：{{ randValue }}</p>

  <button @click="onButtonClick">ボタン</button>
  <p>ランダムな値：{{ randValue }}</p>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
