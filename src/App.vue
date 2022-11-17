<template>
  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i"> {{ a }} </a>
  </div>
  <DiscountEvent />
  <ModalEvent :products="products" :누른거="누른거" :모달창="모달창" @close="모달창 = !모달창" />
  <CardEvent @openModal="detail" 누른거=$event :product=a v-for="(a, i) in products" :key="i" />
</template>

<script>
import data from './data'
import DiscountEvent from '@/components/DiscountEvent'
import ModalEvent from '@/components/ModalEvent'
import CardEvent from '@/components/Card'

export default {
  name: 'App',
  data () {
    return {
      오브젝트: { name: 'kim', age: 20 },
      누른거: 0,
      products: data,
      메뉴들: ['Home', 'Shop', 'About'],
      신고수: [0, 0, 0],
      모달창: false
    }
  },
  methods: {
    increase (i) {
      this.신고수[i]++
    },
    detail (i) {
      this.모달창 = !this.모달창
      this.누른거 = i
    }
  },
  components: { ModalEvent, DiscountEvent, CardEvent }
}
</script>

<style>
body {
  margin: 0
}

div {
  box-sizing: border-box;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
