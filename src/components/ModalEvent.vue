<template>
  <div v-if="모달창" class="black-bg">
    <div class="white-bg">
      <h4>{{ products[누른거].title }}</h4>
      <img :src="products[누른거].image"/>
      <h5>{{ products[누른거].content }}</h5>
      <input v-model.number="month">
      <p> {{ month }} 개월 선택함 {{ products[누른거].price * month }}원</p>
      <button @click="$emit('close')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalEvent',
  data () {
    return {
      month: 1
    }
  },
  updated () {
    if (this.month === 2) {
      alert('2입니다.')
      this.month = 3
    }
  },
  watch: {
    month (month) {
      // 사용자가 month를 글자로 입력하면 경고문
      if (month > 12) {
        alert('최대 12개월 까지 입력해주세요.')
      } else if (isNaN(month)) {
        alert('문자뿌리지마')
        this.month = 1
      }
    }
  },
  props: {
    products: Array,
    누른거: Number,
    모달창: Boolean
  }
}
</script>

<style scoped>
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
