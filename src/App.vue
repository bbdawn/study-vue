// 동적인 UI 만드는 법
// 1. UI의 현재 상태를 데이터로 저장해둠
// 2. 데이터에 따라 UI가 어떻게 보일지 작성

<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4> 
      <p>상세페이지 내용임</p> 
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in menu" :key="a">{{a}}</a>
  </div>

  <div> 
    <img src="./assets/room0.jpg" class="room-img">
    <h4 @click="모달창열렸니 = true">{{products[0]}}</h4>
    <p>{{ price1 }}만원 </p>
    <button @click="increase">허위매물신고</button> <span>신고수 : {{신고수}}</span>
  </div>
  <div>
     <img src="./assets/room1.jpg" class="room-img">
    <h4 class="red" :style="스타일">{{products[1]}}</h4>
    <p>{{ price2 }}만원 </p>
  </div>
   <div>
     <img src="./assets/room2.jpg" class="room-img">
    <h4 class="red" :style="스타일">{{products[2]}}</h4>
    <p>{{ price3 }}만원 </p>
  </div>

</template>

<script>

export default {
  name: 'App',
  data(){
    return{
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
 