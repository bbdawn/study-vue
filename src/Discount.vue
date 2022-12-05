<template>
  <div class="discount">
    <h4>지금 결제하면 {{할인율}}% 할인</h4>
  </div>
</template>

<script>
export default {
    //name은 두 단어 이상으로 작성하기
    name: 'TheDiscount',
    props : {
      할인율 : Number
    }
}
</script>

<style>

</style>