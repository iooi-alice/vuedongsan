<template>
  <div class="black-bg" v-if="isOpen == true">
    <div class="dialog">
      <img class="room-img" :src="oneroomList[productId].image" alt="원룸 내부 이미지" />
      <h4>{{ oneroomList[productId].title }}</h4>
      <p>{{ oneroomList[productId].content }}</p>
      <div><input v-model.number="month" type="text" /> 개월</div>
      <span> {{ month }} 개월 선택함: {{ month * oneroomList[productId].price }} 원</span>
      <div>
        <button @click="$emit('closeModal')">닫기</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductModal',
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(a) {
      if (a >= 13) {
        alert('13이상 입력하지 마세요.');
        this.month = 1;
      }

      if (isNaN(a)) {
        alert('숫자만 입력해야합니다.');
        this.month = 1;
      }
    },
  },
  props: {
    oneroomList: Array,
    productId: Number,
    isOpen: Boolean,
  },
};
</script>

<style>
.black-bg {
  position: fixed;
  top: 0;
  width: 100%;
  height: 100vh;

  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba(0, 0, 0, 0.7);
}

.dialog {
  width: 300px;
  height: 400px;
  padding: 20px;
  border-radius: 8px;
  background: #fff;
}
</style>
