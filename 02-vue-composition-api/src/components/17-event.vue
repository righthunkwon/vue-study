<template>
  <div>
    <input type="text" @keyup.enter="addTodo" @keyup.ctrl.delete="deleteTodo" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">{{ todo }}</li>
    </ul>
  </div>
</template>

<script setup>
/**
 * 키 수식어
 * : .enter, .tab, .delete(delete와 뒤로가기 키), .esc, .space, .up, .down, .left, .right
 */
import { ref } from 'vue'

const todos = ref([])

// 1. enter 키를 눌렀을 때
const addTodo = (event) => {
  /**
   *   아래 if문 코드를 @keyup.enter로 대체하여 간편하게 이벤트 처리 가능
   *
   */
  // if (event.key === 'Enter') {
  //   todos.value.push(event.target.value)
  //   event.target.value = ''
  //   event.target.focus()
  // }

  todos.value.push(event.target.value)
  event.target.value = ''
  event.target.focus()
}

// 2. ctrl + delete 키를 동시에 눌렀을 때
const deleteTodo = (event) => {
  todos.value.pop()
  event.target.value = ''
}
</script>

<style lang="scss" scoped></style>
