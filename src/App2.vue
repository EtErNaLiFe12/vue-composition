<template>
  <h1 @click="increase">
    {{ count }} 
  </h1>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
    let count = ref(0) // 반응성을 가지기 위해 ref라는 기능을 vue에서 가져와서 초기값으로 사용
    function increase() {
      count.value += 1 // 데이터 처럼 활용하기위해 .value를 붙임
    }
    return {
      count,
      increase
    }
  }
}
</script>