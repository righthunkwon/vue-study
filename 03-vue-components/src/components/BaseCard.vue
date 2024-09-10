<template>
  <div class="card-item">
    <div class="card-item-type">{{ computedPostType }}</div>
    <div>{{ props.author }}</div>
    <div>{{ props.title }}</div>
    <div>{{ props.contents }}</div>
    <div>{{ props.createdAt }}</div>
    <div class="card-item-liked">
      <div v-if="props.isLiked">❤️</div>
      <div v-else>🤍</div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
/**
 * defineProps()
 *  - defineProps 함수를 통해 props 선언
 *  - 객체 문법을 활용하여 속성 타입과 함께 선언 가능
 */

/**
 * props
 *  - key: value 구조
 *  - value에는 type을 정의하거나 객체를 둘 수 있음 (typeName || typeObject)
 *  - value에 객체를 둘 경우 type, default, required 등의 여러 속성들을 활용할 수 있음
 *
 */

/**
 * props value property (typeObject)
 *  - type
 *  - default
 *  - required
 *  - validator
 *
 */
const props = defineProps({
  postType: { type: String, default: '기본타입' },
  title: String,
  contents: String,
  author: String,
  createdAt: Number,
  isLiked: Boolean
})

const computedPostType = computed(() => {
  return props.postType === '' ? '기본타입' : props.postType
})
</script>

<style scoped>
.card-item {
  width: 200px;
  margin: 16px;
  padding: 20px;
  font-weight: 600;
  background-color: bisque;
}

.card-item-type {
  margin: 4px;
  padding: 8px;
  color: cornflowerblue;
}

.card-item-liked {
  display: flex;
  justify-content: end;
}
</style>
