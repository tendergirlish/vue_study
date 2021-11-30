<template>
  <div v-for="(product, index) in oneroom" :key="index">
    <div>
      <img :src="oneroom[index].image" alt="룸이미지" class="room_img">
    </div>
    <h4 class="title">{{ oneroom[index].title }} oneroom</h4>
    <p>{{ oneroom[index].price }} won</p>
    <button @click="product.count += 1">허위매물 신고</button>
    <span> 신고수 : {{ product.count }}</span>
  </div>
</template>
<script>
export default {
  name:'product',
  props:{
    oneroom:Array,
    modalstatus: Number,
  },
}
</script>