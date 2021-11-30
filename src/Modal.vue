<template>

  <div v-if="modalstatus == true" class="black_bg">
    <div class="white_bg">
      <h4>{{oneroom[누른거].title}}</h4>
      <img :src="oneroom[누른거].image" alt="상세 이미지">

      <input v-model.number="month" maxlength="3">
<!--      <input @input="month = $event.target.value">-->

      <p>{{ oneroom[누른거].content}} </p>
      <p>{{ month }}개월 선택함 :{{ comma(oneroom[누른거].price * month) }} 원</p>
      <button @click="$emit('closeModal',)" class="modalbtn">
        닫기
      </button>
    </div>
  </div>

</template>

<script>

export default {
  name: 'Modal',
  props: {
    oneroom: Array,
    누른거: Number,
    modalstatus: Boolean,
  },
  data() {
    return {
      month: '',
   }
  },
  watch: {
    month(val) {
      if (isNaN(val) == true) {
        alert('숫자만 입력 하세요.');
        return this.month = this.month.replace(/[^0-9]/g, '');
      }
    },
  },
  methods: {
    // 천단위에 콤마 찍어주는것
   comma (value){
     return String(value).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
   },
  },
  beforeUpdate() {
    if (this.month == 2 || this.month == 1) {
      alert('2개월은 미만 너무 적음.. 최소 3개월 입력해주세요.');
      this.month = 3;
    }
  },
  filters:{
    // comma (value){
    //   return String(value).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    // }
  },
}
</script>
<style>

</style>