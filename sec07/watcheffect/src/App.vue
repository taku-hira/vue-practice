<script setup lang="ts">
import {ref, watchEffect} from 'vue';

// カクテル番号のテンプレート変数を用意
const cocktailNo = ref(1);
// カクテル番号に対応するカクテル情報のテンプレート変数を用意
const priceMsg = ref('');

// cocktailNoを1秒ごとに1~4の乱数を使って変更
setInterval(
  ():void => {
    cocktailNo.value = Math.round(Math.random() * 3) + 1;
  },
  1000
);
interface Cocktail {
  id: number;
  name: string;
  price: number;
}
// watchEffectを設定
watchEffect(
  ():void => {
    priceMsg.value = getCocktailInfo(cocktailNo.value);
  }
);

function getCocktailInfo(cocktailNo: number): string {
  const cocktailDataListInit = new Map<number, Cocktail>();
  cocktailDataListInit.set(4, {id: 4, name: 'マティーニ', price: 1500});
  cocktailDataListInit.set(3, {id: 3, name: 'ビバーレット', price: 1200});
  cocktailDataListInit.set(2, {id: 2, name: 'マウンテンコウサイ', price: 1000});
  cocktailDataListInit.set(1, {id: 1, name: 'ブラックモヒカン', price: 800});

  // カクテル番号に該当するカクテルデータを取得
  const cocktail = cocktailDataListInit.get(cocktailNo);
  let msg = "該当カクテルはありません";
  if (cocktail != undefined) {
    msg = '該当するカクテルは' + cocktail.name + 'で、価格は、' + cocktail.price + '円です。';
  }


  return msg
}
</script>

<template>
  <p>カクテル番号：{{ cocktailNo }}</p>
  <p>カクテル情報：{{ priceMsg }}</p>
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
