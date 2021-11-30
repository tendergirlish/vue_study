<template>
    <div>
      <div>
        <img :src="oneroom.image" alt="룸이미지" class="room_img">
      </div>
      <h4 @click="$emit('openModal',oneroom.id)" class="title">{{ oneroom.title }} oneroom</h4>
      <p>{{ oneroom.price }} won</p>
    </div>

<!--  <div v-for="(product, index) in oneroom" :key="index">-->
<!--    <div>-->
<!--      <img :src="oneroom[index].image" alt="룸이미지" class="room_img">-->
<!--    </div>-->
<!--    <h4 class="title">{{ oneroom[index].title }} oneroom</h4>-->
<!--    <h4 @click="modalstatus = true; 누른거 = index" class="title">{{ oneroom[index].title }} oneroom</h4>-->
<!--    <p>{{ oneroom[index].price }} won</p>-->
    <!--    <button @click="product.count += 1">허위매물 신고</button>-->
    <!--    <span> 신고수 : {{ product.count }}</span>-->
<!--  </div>-->

</template>
<script>
export default {
  props:{
    oneroom: Object,
  }
}
</script>



