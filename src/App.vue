<template>
  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i"> {{ a }} </a>
  </div>
  <DiscountEvent v-if="showDiscount" :discount="discount"/>
  <button @click="sort"> 가격 순 정렬</button>
  <button @click="sortReverse"> 가격 순 역정렬</button>
  <button @click="sortBack"> 되돌리기</button>
  <transition name="fade">
    <ModalEvent :products="products" :누른거="누른거" :모달창="모달창" @close="모달창 = !모달창"/>
  </transition>
  <CardEvent @openModal="detail" 누른거=$event :product=a v-for="(a, i) in products" :key="i"/>
</template>

<script>
import data from './data'
import DiscountEvent from '@/components/DiscountEvent'
import ModalEvent from '@/components/ModalEvent'
import CardEvent from '@/components/Card'

export default {
  name: 'App',
  mounted () {
    const a = setInterval(() => {
      if (this.discount === 0) {
        clearInterval(a)
      } else this.discount -= 1
    }, 1000)
  },
  data () {
    return {
      오브젝트: {
        name: 'kim',
        age: 20
      },
      누른거: 0,
      원룸오리지널: [...data],
      products: data,
      메뉴들: ['Home', 'Shop', 'About'],
      신고수: [0, 0, 0],
      모달창: false,
      showDiscount: true,
      discount: 30
    }
  },
  methods: {
    increase (i) {
      this.신고수[i]++
    },
    detail (i) {
      this.모달창 = !this.모달창
      this.누른거 = i
    },
    sort () {
      this.products.sort((a, b) => {
        return a.price - b.price
      })
    },
    sortReverse () {
      this.products.sort((a, b) => {
        return b.price - a.price
      })
    },
    sortBack () {
      this.products = [...this.원룸오리지널]
    }
  },
  components: {
    ModalEvent,
    DiscountEvent,
    CardEvent
  }
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

.fade-enter-from {
  transform: translateY(-100px);
}

.fade-enter-active {
  transition: all 1s;
}

.fade-enter-to {
  transform: translateY(0px);
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 1s;
}

.fade-leave-to {
  opacity: 0;
}

</style>
