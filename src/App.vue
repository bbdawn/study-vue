<template>

  <div class="menu">
    <!-- v-for="작명 in 몇회" -->
    <!-- :key=""의 용도 => 반복문 쓸 때 꼭 써야함. 반복문 돌린 요소를 컴퓨터가 구분하기 위해 씀  -->
    <!-- <a v-for="작명 in menu" :key="작명">{{작명}}</a> -->
    <!-- Vue 반복문은 2개까지 가능. 왼쪽 변수는 array 내의 데이터, 오른쪽 변수는 1씩 증가하는 정수  -->
    <a v-for="(a,i) in menu" :key="i">{{a}}</a>
  </div>


  <img alt="Vue logo" src="./assets/logo.png">

  <div>
    <h4 class="red" :style="스타일">{{products[0]}}</h4>
    <p>{{ price1 }}만원 </p>
    <button @click="increase">허위매물신고</button> <span>신고수 : {{신고수}}</span>
  </div>
  <div>
    <h4 class="red" :style="스타일">{{products[1]}}</h4>
    <p>{{ price2 }}만원 </p>
  </div>
   <div>
    <h4 class="red" :style="스타일">{{products[2]}}</h4>
    <p>{{ price3 }}만원 </p>
  </div>

</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      신고수 : 0,
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

</style>
