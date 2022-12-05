// HTML 태그 안의 속성 데이터바인딩은 :블라블라
// HTML 태그 안의 내용 데이터바인딩은 {{블라블라}}
// v-for, v-if, v-else-if

<template>

  <div v-if="1==2">
    안녕하세요
  </div>
  <div v-else-if="1==3">
    안녕하세요222
  </div>
  <div v-else>
    안녕하세요333
  </div>



  <!-- 방법1. class명을 조건부로 넣으려면 {클래스명:조건} 모달창열렸니가 true일때만 end를 부착  -->
  <!-- <div class="start" :class="{end : 모달창열렸니 }"> 
  <Modal @closeModal="모달창열렸니=false" 
    :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니"/>
  </div> -->

  <!-- 방법2. transition -->
  <Transition name="fade"> 
    <Modal @closeModal="모달창열렸니=false" 
    :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니"/>
  </Transition>




  <div class="menu">
    <a v-for="a in menu" :key="a">{{a}}</a>
  </div> 

  <Discount v-bind="오브젝트" />
  <!-- <Discount :이름="오브젝트.name" :나이="오브젝트.age"/> -->
  <button @click="priceSort">가격순정렬</button>
  <br>


  
  <Card @openModal="모달창열렸니 = true; 누른거 = $event"  :원룸="원룸들[i]" v-for="(작명,i) in 원룸들" :key="작명"/>
  

 

</template>

<script>

import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data(){
    return{
      오브젝트 : { name : 'kim', age : 20 },
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      price1 : 50,
      price2 : 60,
      price3 : 70,
      스타일 : 'color : blue',
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      menu : ['Home', 'Shop', 'About'],
    }
  },
  methods : {
    increase(){ 
        this.신고수 += 1;
    },
    priceSort(){
      // var array = [3,5,2];
      // array.sort();
      // console.log(array);

      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })   
    },
  },
  components: {
    Discount,
    Modal,
    Card,
   
  }
}
</script>

<style>
body {
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background : rgba(0,0,0,0.5);
  position: fixed; padding:20px;
}
.white-bg {
  width:100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 30%;
  margin-top: 40px;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}


.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}

/* 입장 */
.fade-enter-from{ 
  /* 시작 때 스타일 */
  opacity: 0;
}
.fade-enter-active{
  /* transition */
  transition: all 1s;
}
.fade-enter-to{
  /* 끝날 때 스타일 */
  opacity: 1;
}

/* 퇴장 */
.fade-leave-from{ 
  /* 시작 때 스타일 */
  opacity: 1;
}
.fade-leave-active{
  /* transition */
  transition: all 1s;
}
.fade-leave-to{
  /* 끝날 때 스타일 */
  opacity: 0;
}


</style>
 