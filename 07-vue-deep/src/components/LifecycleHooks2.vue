<template>
  <div>
    <h2>Lifecycle Hooks2</h2>
  </div>
</template>

<script setup>
/**
 * Lifecycle
 * : 컴포넌트가 생성, 장착, 변경, 소멸되는 단계
 *
 * Lifecycle Hooks
 * : 컴포넌트의 라이프사이클의 각 단계별로 개발자가 접근할 수 있게 해주는 함수
 * : setup > (beforeCreate > creted) > beforeMount > mounted
 *   > (beforeUpdate > updated) > beforeUnmount > unmounted
 *
 * : comopsition api에서는 options api와 달리
 *   1) beforeCreate와 created 훅 대신 setup 내부에서 사용하면 되고,
 *   2) 라이프사이클 훅에 접두사 on을 붙여서 사용한다.
 *
 */

/**
 * Mounting
 * : DOM에 컴포넌트를 삽입하는 단계
 * : 서버 렌더링에서 지원되지 않으며 초기 렌더링 직전에 DOM 변경 시 활용
 *
 *  - onBeforeMount  : 컴포넌트 마운트 직전에 호출 (대부분 사용 권장 X)
 *  - onMounted      : 컴포넌트 마운트 완료 후 호출 (DOM 접근 가능),
 *                     (*모든 자식 컴포넌트까지 마운트된 상태)
 *                     (*자체 DOM 트리가 생성되어 상위 컴포넌트에도 삽입된 상태)
 *
 */
</script>

<style scoped></style>
