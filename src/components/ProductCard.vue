<template>
  <div v-for="product in oneroomList" :key="product.id">
    <h2>{{ product.id }}</h2>
    <img class="room-img" :src="product.image" alt="원룸 내부 이미지" />
    <h4 @click="send(product)">{{ product.title }}</h4>
    <p>{{ product.content }}</p>
    <span>{{ product.price }} 원</span>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    oneroomList: Array,
  },
  methods: {
    send(product) {
      this.$emit('openModal', product.id);
    },
  },
};
</script>

<style>
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
