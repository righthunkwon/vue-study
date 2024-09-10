<template>
  <div>
    <h2>computed</h2>
    <!-- 1. template syntax: 간단히 사용하면 편리, 단, 코드가 길어질 경우 가독성이 떨어지고 유지보수가 어려움 -->
    <p>{{ teacher.name }}</p>
    <p>{{ teacher.lectures.length > 0 ? '강의가 존재합니다.' : '강의가 존재하지 않습니다.' }}</p>
    <!-- 2. computed: 캐시 처리되어 성능 면에서 유리 -->
    <p>{{ hasLectureComp }}</p>
    <p>{{ hasLectureComp }}</p>
    <p>{{ hasLectureComp }}</p>
    <!-- 3. method: 매번 호출되어 성능 면에서 불리 -->
    <p>{{ hasLectureFunc() }}</p>
    <p>{{ hasLectureFunc() }}</p>
    <p>{{ hasLectureFunc() }}</p>
  </div>
</template>

<script>
import { reactive, computed } from 'vue'

export default {
  setup() {
    const teacher = reactive({
      name: '권정훈',
      lectures: ['HTML/CSS', 'JavaScript', 'Vue3']
    })

    const hasLectureComp = computed(() => {
      console.log('computed 호출 !!!') // 1번 호출
      return teacher.lectures.length > 0 ? '강의가 존재합니다.' : '강의가 존재하지 않습니다.'
    })

    const hasLectureFunc = () => {
      console.log('method 호출 !!!') // 3번 호출
      return teacher.lectures.length > 0 ? '강의가 존재합니다.' : '강의가 존재하지 않습니다.'
    }

    return { teacher, hasLectureComp, hasLectureFunc }
  }
}
</script>

<style lang="scss" scoped></style>
