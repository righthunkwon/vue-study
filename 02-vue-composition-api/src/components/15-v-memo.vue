<template>
  <div>
    <!-- 1. normal component-->
    <h2>일반 컴포넌트</h2>
    <div>
      <p>subscribers: {{ subscribers }}</p>
      <p>views: {{ views }}</p>
      <p>likes: {{ likes }}</p>
    </div>
    <hr />

    <!-- 2. v-memo component -->
    <!-- 성능 최적화에 사용, 일반적으로 목록 렌더링 시 길이가 1000개 이상일 때 사용 -->
    <!-- 배열 내부에 정의한 값의 상태가 변할 경우에만 컴포넌트를 업데이트 함으로써 필요할 때만 컴포넌트를 업데이트 -->
    <h2>v-memo 컴포넌트</h2>
    <div v-memo="[subscribers]">
      <p>subscribers: {{ subscribers }}</p>
      <p>views: {{ views }}</p>
      <p>likes: {{ likes }}</p>
    </div>
    <hr />

    <!-- 테스트 버튼 -->
    <button @click="subscribers++">Subs++</button>
    <button @click="views++">Views++</button>
    <button @click="likes++">Likes++</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const subscribers = ref(4000)
    const views = ref(400)
    const likes = ref(20)

    return { subscribers, views, likes }
  }
}
</script>

<style lang="scss" scoped></style>
