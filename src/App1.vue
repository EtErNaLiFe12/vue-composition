<template>
  <h1 @click="increase">
    {{ count }}
  </h1>
  <h1 @click="changeMessage">
    {{ message }}
  </h1>
</template>

<script>
import { ref, computed, watch, onMounted } from 'vue'

export default {
    setup() { // setup 내부에 작성되는 내용은 lifecycle에서 created와 시점이 같음.
    const count = ref(0)
    const doubleCount = computed(() => {
      return count.value * 2
    })
    function increase() {
      count.value += 1
    }

    const message = ref('Hello world!')
    const reversedMessage = computed(() => {
      return message.value.split('').reverse().join('')
    })
    watch(message, newValue => {
      console.log(newValue)
    })
    function changeMessage() {
      message.value = 'Good?!'
    }
    console.log(this.message)

    onMounted(() => {
      console.log(count.value)
    })
    return {
      count,
      doubleCount,
      increase,
      message,
      reversedMessage,
      changeMessage
    }
  }
}
</script>