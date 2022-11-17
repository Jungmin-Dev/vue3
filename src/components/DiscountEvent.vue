<template>
  <div class="discount">
    <h4>지금 결제하면 {{ discount }}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: 'DiscountEvent',
  props: {
    discount: Number
  }
}
</script>

<style scoped>
.discount {
  background: gray;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
