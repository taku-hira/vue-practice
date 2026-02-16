<script setup lang="ts">
import { ref } from 'vue';

const inputNameModel = ref('双方向');

const inputNameBind = ref('しんちゃん')
const inputNameOn = ref('ななし')

const onInputName = (event: Event):void => {
  const element = event.target as HTMLInputElement;
  inputNameOn.value = element.value;
}
</script>

<template>
  <section>
    <input type="text" v-model="inputNameModel">
    <p>入力された値：{{ inputNameModel }}</p>
  </section>

  <section>
    <input type="text" v-bind:value="inputNameBind" v-on:input="onInputName">
    <p>入力された値：{{ inputNameBind }}</p>
  </section>

  <section>
    <input type="text" v-on:value="inputNameOn">
    <p>入力された値：{{ inputNameOn }}</p>
  </section>
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
