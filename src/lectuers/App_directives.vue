<template>
  <!-- 디렉티브 v- 접두사가 있는 특수 속성 -->
  <div>
    <p>{{ msg }}</p>
    <p v-text="msg"></p>
    <p v-text="htmlStr"></p>
    <p v-html="htmlStr"></p>
    <hr>
    <!-- v-once 한번만 랜더링 함 이후 변경X -->
    <p v-once>{{ msg }} !!!</p>
    <hr>
    <!-- v-memo -->
    <div v-once>
      <p>subscribers: {{ subscribers }}</p>
      <p>views: {{ views }}</p>
      <p>likes: {{ likes }}</p>
    </div>
    <button v-on:click="subscribers++">subscribers ++</button>
    <button v-on:click="views++">views ++</button>
    <button v-on:click="likes++">likes ++</button>
    <br>
    <!-- v-memo: 데이터 변경이 일어나면 동작 성능 최적화때때 사용 공식문서 참고 -->
    <div v-memo="[subscribers, views]">
      <p>subscribers: {{ subscribers }}</p>
      <p>views: {{ views }}</p>
      <p>likes: {{ likes }}</p>
    </div>
    <button v-on:click="subscribers++">subscribers ++</button>
    <button v-on:click="views++">views ++</button>
    <button v-on:click="likes++">likes ++</button>
    <div>
      <p>subscribers: {{ subscribers }}</p>
      <p>views: {{ views }}</p>
      <p>likes: {{ likes }}</p>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    const msg = ref('안녕하세요')
    const htmlStr = ref('<strong>Vue3!!!</strong>')
    const subscribers = ref(4000)
    const views = ref(400)
    const likes = ref(2)

    return {
      msg,
      htmlStr,
      subscribers,
      views,
      likes,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>