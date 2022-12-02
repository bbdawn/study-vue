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

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>{{원룸들[누른거].title}}</h4> 
       <img :src="원룸들[누른거].image" >
      <p>{{원룸들[누른거].content}}</p> 
      <p>{{원룸들[누른거].price}}원</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in menu" :key="a">{{a}}</a>
  </div> 

  <div v-for="(a,i) in 원룸들" :key="i"> 
    <img :src="a.image" class="room-img">
    <h4 @click="모달창열렸니 = true; 누른거 = i">{{a.title}}</h4>
    <p>{{a.price}}원 </p>
  </div>

</template>

<script>

import data from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return{
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
    }
  },
  components: {
   
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
</style>
 