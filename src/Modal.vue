// props는 read-only임. 받아온 거 수정할 수 없음 

<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>{{원룸들[누른거].title}}</h4> 
       <img :src="원룸들[누른거].image" >
      <p>{{원룸들[누른거].content}}</p> 

      <!-- input 방법1 -->
      <!-- <input @input="month = $event.target.value"> -->
      <!-- input 방법2 -->
      <input v-model="month">
      <p>{{month}}개월 선택함 : {{원룸들[누른거].price * month}}원</p>
      <!-- <button @click="모달창열렸니 = false">닫기</button> -->
   <button @click="$emit('closeModal')">닫기</button>
    </div>
    
  </div>
</template>

<script>
export default {
    name: 'TheModal',
    data(){
      return {
        month : 1,
      }
    },
    props: {
        원룸들 : Array,
        누른거 : Number,
        모달창열렸니 : Boolean,
    }
}
</script>

<style>

</style>