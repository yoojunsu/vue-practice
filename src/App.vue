<template>
  <VuedongsanHeader />
  <DiscountBanner />
  <ProductModal @closeModal="상세페이지모달상태 = false;" :판매상품데이터="판매상품데이터" :선택상품idx="선택한상품Idx" :상세페이지모달상태="상세페이지모달상태" />
  <div class="room-cont-wrap">
    <VuedongsanContent @openModal="상세페이지모달상태 = true; 선택한상품Idx = $event" :판매상품데이터="판매상품데이터[index]" v-for="(판매상품컨텐츠,index) in 판매상품데이터" :key="index" />
  </div>
</template>

<script>
import VuedongsanHeader from './components/vuedongsan-header.vue';
import DiscountBanner from "./components/discount-banner.vue";
import ProductModal from './components/product-modal.vue';
import VuedongsanContent from './components/vuedongsan-content.vue';

//판매상품 데이터 
import VuedongsanData from './assets/data.js';
VuedongsanData;

export default {
  name: 'App',
  data() {
    return {
      상세페이지모달상태: false,
      선택한상품Idx: 0,
      판매상품데이터: VuedongsanData,
    }
  },
  components: {
    VuedongsanHeader: VuedongsanHeader,
    DiscountBanner: DiscountBanner,
    ProductModal: ProductModal,
    VuedongsanContent: VuedongsanContent
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  list-style: none;
  color: #000;
}

a {
  color: #000;
  text-decoration: none;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}

img {
  width: 100%;
}

header span {
  position: absolute;
  text-indent: -9999px;
}

header img  {
  max-width: 100px;
}

header nav {
  display: flex;
  justify-content: center;
  gap: 75px;
  background: darkslateblue;
  max-width: 80%;
  margin: 0 auto 30px;
  border-radius: 20px;
}

header nav a {
  color: #fff;
  padding: 20px 0;
}

.room-cont-wrap {
    display: grid;
    grid-template-areas: ". . .";
    grid-auto-columns: 1fr;
    gap: 50px 30px;
    width: 80%;
    margin: 0 auto;
    margin-bottom: 50px;
}
</style>
