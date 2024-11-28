<template>
  <div>
    <h2>{{ teacher.name }}</h2>
    <h3>강의가 있습니까?</h3>
    <!-- <p>{{ teacher.lectures.length > 0 ? '있음' : '없음' }}</p> -->
    <p>{{ hasLecture }}</p>
    <p>{{ existLecture() }}</p>
    <p>{{ existLecture() }}</p>
    <button v-on:click="counter++">count : {{ counter }}</button>
    <h2>이름</h2>
    <p>{{ fullName }}</p>
  </div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
  setup () {
    const teacher = reactive({
      name: '짐코딩',
      lectures: [
        'HTML/CSS',
        'Javascript',
        'Vue3'
      ]
    })

    const hasLecture = computed(() => teacher.lectures.length > 0 ? '있음' : '없음' ) // 캐쉬됨 컴포넌트가 새롭게 랜더링 되도 캐쉬내용을 가져옴
    const existLecture = () => teacher.lectures.length > 0 ? '있음' : '없음'  // 캐쉬 안됨 컴포넌트가 새롭게 랜더링 되면 자원낭비
    const counter = ref(0)

    const firstName = ref('홍')
    const lastName = ref('길동')
    const fullName = computed({
      get() {
        return firstName.value + ' ' + lastName.value
      },
      set(value) {
        [firstName.value, lastName.value] = value.split(' ')
      }
    })
    fullName.value = '짐 코딩'

    return {
      teacher,
      hasLecture,
      existLecture,
      counter,
      fullName
    }
  }
}
</script>

<style lang="scss" scoped>

</style>