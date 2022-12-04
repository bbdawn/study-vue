<template>
  
    <img :src="원룸.image" class="room-img">
    <h4 @click="$emit('openModal')">{{원룸.title}}</h4>
    <p>{{원룸.price}}원 </p> 
 
</template>

<script>
export default {
    name: 'TheCard',
    props : {
        원룸 : Object
    
    }

}
</script>

<style>

</style>