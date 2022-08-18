<template>
  <div>
    <h1>{{ $t('home.title') }} - {{$i18n.locale}}</h1>
    <p>test</p>
  </div>
</template>

<style>
/* 全体的なスタイル
/* カルーセルをカスタマイズ
-------------------------------------------------- */

/* カルーセルの基本クラス */
.carousel {
  margin-bottom: 4rem;
}
/* 画像を配置しているので、キャプションを手助けする必要がある */
.carousel-caption {
  bottom: 3rem;
  z-index: 10;
}

/* img要素の配置のために高さを宣言 */
.carousel-item {
  height: 32rem;
}
.carousel-item > img {
  position: absolute;
  top: 0;
  left: 0;
  min-width: 100%;
  height: 32rem;
}

/* カルーセルの下の3列の中のテキストを整列 */
.marketing .col-lg-4 {
  margin-bottom: 1.5rem;
  text-align: center;
}
.marketing h2 {
  font-weight: 400;
}
.marketing .col-lg-4 p {
  margin-right: 0.75rem;
  margin-left: 0.75rem;
}

/* フィーチャー
------------------------- */

.featurette-divider {
  margin: 5rem 0; /* ブートストラップの&lt;hr&gt;をもっと外に出す */
}

/* マーケティングの見出しを細めにする */
.featurette-heading {
  font-weight: 300;
  line-height: 1;
  letter-spacing: -0.05rem;
}

/* 背景 */
.bg-img {
  background-image: url('https://hasebetest.g.kuroco-img.app/v=1234567890/files/user/Image/29_ext_01_0.png');
  background-size: cover;
  background-position: center 60%;
}

/* レスポンシブCSS
-------------------------------------------------- */

@media (min-width: 40em) {
  .featurette-heading {
    font-size: 50px;
  }
}

@media (min-width: 62em) {
  .featurette-heading {
    margin-top: 7rem;
  }
}
</style>

<script>
export default {
  async asyncData({ $axios, app, $config }) {
  console.log('baseURL=' + process.env.BASE_URL);
  console.log('API_SECRET=' + $config.apiSecret);
  console.log('BASE_ORIGIN=' + $config.baseOrigin);
    if(app.i18n.locale === 'ja'){
      try {
       const response = await $axios.$get(
         process.env.BASE_URL + '/rcms-api/14/top/1002'
       )
       console.log(response)
       return { response }
      } catch (e) {
       console.log(e.message)
       }
    }
    else{
      try {
       const response = await $axios.$get(
         process.env.BASE_URL + '/rcms-api/14/top/1002?_lang=en'
       )
       console.log(response)
       return { response }
      } catch (e) {
        console.log(e.message)
       }
    }
  },
}
</script>
