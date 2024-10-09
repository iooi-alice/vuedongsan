<template>
  <header class="nav">
    <nav>
      <a href="/" v-for="navItem in navList" :key="navItem">{{ navItem }}</a>
    </nav>
  </header>
  <DiscountPopup />

  <ProductCard
    @openModal="
      isOpen = true;
      productId = $event;
    "
    :oneroomList="oneroomList"
    :openModal="openModal"
  />
  <ProductModal @closeModal="isOpen = false" :oneroomList="oneroomList" :productId="productId" :isOpen="isOpen" />
</template>

<script>
import data from './assets/oneroom';
import DiscountPopup from './components/DiscountPopup';
import ProductModal from './components/ProductModal';
import ProductCard from './components/ProductCard';

export default {
  name: 'App',
  data() {
    return {
      productId: 0,
      oneroomList: data,
      isOpen: false,
      countList: [0, 0, 0],
      products: [
        { city: '역삼동 원룸', cost: '50만원', image: require('@/assets/room0.jpg') },
        { city: '천호동 원룸', cost: '60만원', image: require('@/assets/room1.jpg') },
        { city: '마포구 원룸', cost: '70만원', image: require('@/assets/room2.jpg') },
      ],
      navList: ['Home', 'Products', 'About', 'Shop'],
    };
  },
  methods: {
    increase(i) {
      this.countList[i]++;
    },
  },
  components: {
    DiscountPopup,
    ProductModal,
    ProductCard,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.nav {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.nav a {
  color: #fff;
  padding: 10px;
  text-decoration: none;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
