<template>
  <div v-for="post in posts" :key="post.id">
    <BaseCard
      :postType="post.postType"
      :title="post.title"
      :contents="post.contents"
      :author="post.author"
      :createdAt="post.createdAt"
      :isLiked="post.isLiked"
    ></BaseCard>
  </div>
</template>

<script setup>
/**
 * v-for과 props를 활용한 컴포넌트 재사용
 * posts는 api 호출 결과에 해당하는 데이터라 가정
 *
 */
import BaseCard from '@/components/BaseCard.vue'
import { reactive } from 'vue'

const posts = reactive([
  {
    id: 1,
    postType: '', // 기본타입
    title: '제목1',
    contents: '내용1',
    author: '작성자1',
    createdAt: 20240808,
    isLiked: true
  },
  {
    id: 2,
    // postType: null, // 기본타입
    title: '제목2',
    contents: '내용2',
    author: '작성자2',
    createdAt: 20240809,
    isLiked: false
  },
  {
    id: 3,
    postType: '타입B',
    title: '제목3',
    contents: '내용3',
    author: '작성자3',
    createdAt: 20240810,
    isLiked: true
  },
  {
    id: 4,

    postType: '타입C',
    title: '제목4',
    contents: '내용4',
    author: '작성자4',
    createdAt: 20240811,
    isLiked: true
  },
  {
    id: 5,
    postType: '타입A',
    title: '제목5',
    contents: '내용5',
    author: '작성자5',
    createdAt: 20240812,
    isLiked: false
  }
])
</script>

<style lang="scss" scoped></style>
