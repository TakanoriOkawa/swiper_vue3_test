<!-- npm i swiper → vue.3// swiperモジュールはvue3から使える。
（公式）https://swiperjs.com/vue
demoが豊富なので参考になる。
-->

<template>
  <!-- :slides-pre-view 表示するカードの数
       :space-between 数値がmargin-rightになる。
       :loop ループ
       :autoplay="{}" 自動スライド、オブジェクト内にスライド速度などを入れる。
       @swiper swiperが読み込まれた時
       @slideChage スライドした際のメソッド。
   -->
  <h1>swiper.jsを使う</h1>
  <swiper
    :slides-per-view="1"
    :space-between="0"
    :autoplay="{ delay: 2500, disableOnInteraction: false }"
    :loop="true"
    navigation
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >
    <swiper-slide
      >Slide 1
      <img src="../assets/image_1.jpg" />
    </swiper-slide>
    <swiper-slide
      >Slide 2
      <img src="../assets/image_2.jpg" />
    </swiper-slide>
    <swiper-slide
      >Slide 3
      <img src="../assets/image_3.jpg" />
    </swiper-slide>
    ...
  </swiper>
</template>
<script>
// 使うモジュールをインストール
import SwiperCore, { Navigation, Autoplay } from "swiper";

// vue.js用のコンポーネントを読み込む
import { Swiper, SwiperSlide } from "swiper/vue";

// スタイルもモジュールから読み込む
import "swiper/swiper.scss";
import "swiper/components/navigation/navigation.scss";

// モジュールをインストールする。登録
SwiperCore.use([Navigation, Autoplay]);

// Import Swiper styles
export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  methods: {
    onSwiper(swiper) {
      console.log(swiper);
    },
    onSlideChange() {
      console.log("slide change");
    },
  },
};
</script>

<style lang="scss" scoped>
// swiperの全体スタイル
.swiper-container {
  width: 300px;
  height: 300px;
}

// スライドの各カードのスタイル
.swiper-slide {
  & > img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
