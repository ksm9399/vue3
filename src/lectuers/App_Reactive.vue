  <template>
    <div>
      <button v-on:click="state.count++">Click state {{ state.count }}</button>
      <button v-on:click="increment">Click increment {{ state.count }}</button>
      <button v-on:click="increment">Click increment Deep {{ state.deep.count }}</button>
    </div>
  </template>

<script>
import { reactive } from 'vue';

export default {
  setup() {
    const state = reactive({
      count: 0,
      deep: {
        count: 0
      }

    })
    const increment = () => {
      state.count++
      state.deep.count++
    }

    return {
      state,
      increment
    }
  }
}
</script>

<style lang="scss" scoped></style>