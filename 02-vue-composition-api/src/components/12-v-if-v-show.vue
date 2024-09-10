<template>
  <div>
    <h2 v-if="titleType === 'A'">A제목</h2>
    <h2 v-else-if="titleType === 'B'">B제목</h2>
    <h2 v-else-if="titleType === 'C'">C제목</h2>
    <h2 v-else>D제목</h2>

    <button @click="titleType = 'A'">A</button>
    <button @click="titleType = 'B'">B</button>
    <button @click="titleType = 'C'">C</button>
    <button @click="titleType = 'D'">D</button>
    <hr />

    <!-- 
      v-if는 조건이 참인 경우만 렌더링되어 초기 비용은 낮지만 반복적인 전환비용이 높은 반면, 
      v-show는 CSS기반 전환이 되므로(display 속성) 전한비용은 적지만 초기 렌더링 비용이 높다. 
    -->
    <!-- 
      변화가 잦은 컴포넌트의 경우 v-if보다 v-show가 효율적이고, 
      변화가 적은 컴포넌트의 경우 v-show보다 v-if가 효율적이다 
    -->
    <div v-if="isVisible">
      <h1>Visible(v-if)</h1>
      <p>Paragraph 1</p>
      <p>Paragraph 2</p>
    </div>

    <div v-show="isVisible">
      <h1>Visible(v-show)</h1>
      <p>Paragraph 1</p>
      <p>Paragraph 2</p>
    </div>

    <button @click="toggleVisible">toggleVisible</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const titleType = ref('A')
    const isVisible = ref(true)
    const toggleVisible = () => {
      isVisible.value = !isVisible.value
    }
    return { titleType, isVisible, toggleVisible }
  }
}
</script>

<style lang="scss" scoped></style>
