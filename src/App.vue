<template>
<!-- modal -->
  <transition name="fade" >
    <Modal @CloseModal="modalstatus = false;"
           :oneroom="oneroom"
           :누른거="누른거"
           :modalstatus="modalstatus" />
  </transition>

<!-- nav menu -->
  <div class="menu">
    <a v-for="(mainmenu , i) in menus" :key="i">
      {{ mainmenu }}
    </a>
  </div>

<!-- event box -->
  <Discount v-if="showDiscount" :amount="amount" />

  <!-- sort btn -->
  <div class="sortbtn">
    <button @click="pricesort">가격순 정렬</button>
    <button @click="priceReverse">가격역순 정렬</button>
    <button @click="namesort">이름 오름차순 정렬</button>
    <button @click="nameReverse">이름 내림차순 정렬</button>
    <button @click="sortback">되돌리기</button>
  </div>

<!-- card -->
  <Card @openModal="modalstatus = true; 누른거 = $event"
        :oneroom="oneroom[index]"
        v-for="(product , index) in oneroom" :key="index" />
</template>

<script>
import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';


export default {
  name: 'App',
  data() {
    return{
      amount:30,
      showDiscount:true,
      oneroomOriginal : [...data],
      modalstatus:false,
      menus: ['Home','Product','About'],
      oneroom : data,
      누른거:0,
    }
  },
  methods: {
    sortback(){
      this.oneroom =[...this.oneroomOriginal]; // option filter reset
      console.log('되돌리기');
    },

    priceReverse(){ // 가격 역순
      this.oneroom.sort(function(a,b){
        return b.price - a.price
      })
    },

    pricesort(){ // 가격순
      this.oneroom.sort(function(a,b){
        return a.price - b.price
      })
    },

    namesort(){ // 타이틀 오름차순
      this.oneroom.sort(function(a,b){
          return a.title < b.title ? -1 : a.title > b.title ? 1 : 0;
      })
    },

    nameReverse(){ // 타이틀 내림차순
      this.oneroom.sort(function(a,b){
        return a.title > b.title ? -1 : a.title < b.title ? 1 : 0;
      })
    },
  },
  created() {
    //html 생성전 에이젝스 여기다 넣음
  },
  mounted() {
    //마운트가 됐을때,
    // setTimeout(()=>{
    //   this.showDiscount = false;
    // },2000);

    //discount
    const that = this
    setInterval(()=>{

      if(that.amount >= 1) {
        that.amount--;
      }else{
        that.showDiscount = false;
        clearInterval();
      }
    },1000);
  },
  components: {
    Discount: Discount,
    Modal : Modal,
    Card : Card,
  },
}
</script>
<style>
#app{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
body {
  margin:0;
}
div {
  box-sizing: border-box;
}
.menu{
  background-color: darkslateblue;
  padding:15px;
  border-radius: 5px;
}
.menu a{
  color:white;
  padding:10px;
  cursor: pointer;
}
.menu a:hover{
  opacity: 0.5;
}
.title{
  cursor:pointer;
}
.room_img {
  width:100%;
  margin-top: 40px;
}
.black_bg{
  width:100%; height:100%;
  background-color: rgba(0,0,0,0.5);
  position: fixed;
  padding:20px;
}
.white_bg{
  width:100%; background-color: white;
  border-radius: 8px;
  padding: 20px;
}
.white_bg > img {
  margin:0 auto;
  width:100%;
}
.modalbtn {
    width:50%;
    border:none;
    padding: 5px 0 ;
    background-color:honeydew;
    border-radius: 5px;
  }
.modalbtn:hover{
  background-color: aquamarine;
  color:#2c3e50;
}
.fade-enter-from{
  opacity: 0;
}
.fade-enter-active{
  transition: all 0.7s;
}
.fade-enter-to{
  opacity: 1;
}
.fade-leave-from{
  opacity: 1;
}
.fade-leave-active{
  transition: all 0.7s;
}
.fade-leave-to{
  opacity: 0;
}

.sortbtn > button{
  border:none;
  margin:2px;
  border-radius: 5px;
  background-color:lightpink;
  color: darkslateblue;
  padding:7px;

  cursor:  pointer;
}
.sortbtn > button:last-child{
  margin: 0 auto;
  background: slateblue;
  color:#fff;
}
</style>
