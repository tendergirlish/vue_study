<template>
  <!-- event box -->
  <div class="st">
    <h4>지금 결제하면 {{ amount }}% 할인</h4>
  </div>

</template>
<script>
export default {
  name:'Discount',
  props:{
    amount: Number,
  },
  data() {
    return{

    }
  },
}//end
</script>
<style>
.st{
  color:#fff;
  background-color: slateblue;
  padding:10px;
  margin:10px;
  border-radius: 5px;
}
</style>