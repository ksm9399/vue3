<template>
  <div>
    <h2 v-if="visble">Hello Vue3 True</h2>
    <h2 v-else>Hello Vue3 False</h2>
    <button v-on:click="visble = !visble">toggle</button>
    <hr>
    <h2 v-if="type === 'A'">A입니다.</h2>
    <h2 v-else-if="type === 'B'">B입니다.</h2>
    <h2 v-else-if="type === 'C'">C입니다.</h2>
    <h2 v-else>A, B, C가 아닙다.</h2>
    <button v-on:click="type = 'A'">A</button>
    <button v-on:click="type = 'B'">B</button>
    <button v-on:click="type = 'C'">C</button>
    <button v-on:click="type = 'D'">D</button>
  </div>
  <hr>
  <template v-if="visble">
    <h1>Title</h1>
    <p>Paragraph 1</p>
    <p>Paragraph 2</p>
    <p></p>
  </template>
  <hr>
  <h1 v-show="ok">타이틀 입니다.</h1>
  <button v-on:click="ok = !ok">show toggle</button>
</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    const visble = ref(false)
    const type = ref('A')
    const ok = ref(true)

    return {
      visble,
      type,
      ok
    }
  }
}
</script>

<style lang="scss" scoped>

</style>