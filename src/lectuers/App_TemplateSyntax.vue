<template>
  <div>
    <h2>보간법</h2>
    <p>{{ message }}</p>
    <p v-once>{{ message }}</p>
    <button v-on:click="message = message + '!'">click</button>
    <hr>
    <h2>v-html</h2>
    <p v-html="rawHtml"></p>
    <hr>
    <h2>속성 바인딩</h2>
    <p v-bind:title="dynamicTitle">마우스 오버</p>
    <input type="text" value="홍길동" v-bind:disabled="isInputDisabled">
    다중 속성 바인딩<input v-bind="attrs">
    <hr>
    <h2>js</h2>
    <p>{{ message.split('').reverse().join() }}</p>
    <p>{{ isInputDisabled ? '예' : '아니오' }}</p>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const message = ref('안녕하세요!')
    const rawHtml = ref('<strong>안녕하세요</strong>')
    const dynamicTitle = ref('안녕하세요!!!!')
    const isInputDisabled = ref(false)
    const attrs = ref({
      type: 'text',
      value: '123456',
      disabled: false
    })


    return {
      message,
      rawHtml,
      dynamicTitle,
      isInputDisabled,
      attrs
    }
  }
}
</script>

<style lang="scss" scoped></style>