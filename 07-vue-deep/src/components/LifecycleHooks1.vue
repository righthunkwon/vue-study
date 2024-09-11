<template>
  <div>
    <h2>Lifecycle Hooks1</h2>
  </div>
</template>

<script>
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
 * Creation
 * : 컴포넌트 초기화 단계, 라이프사이클 단계에서 가장 먼저 실행
 * : 서버 렌더링에서 지원되는 단계로 아직 컴포넌트가 DOM에 추가되기 전이므로 DOM에 접근할 수 없음
 *
 *  - beforeCreate  : 컴포넌트 인스턴스 초기화 시 실행 (data() 혹은 computed 처리 이전에 실행되어 접근 불가)
 *  - created       : 컴포넌트 인스턴스 초기화 완료 후 실행 (data() 혹은 computed에 접근 가능)
 *  - setup         : composition api에서 활용, beforeCreate와 created보다 먼저 실행되며 이들을 대체
 *
 */

export default {
  setup() {
    console.log('setup')
    // console.log(this.dataMsg) // error
  },
  data: () => ({
    dataMsg: 'dataMsg'
  }),
  beforeCreate() {
    console.log('beforeCreate')
    console.log(this) // 컴포넌트 인스턴스 접근 가능
    console.log(this.dataMsg) // undefined
  },
  created() {
    console.log('created')
    console.log(this) // 컴포넌트 인스턴스 접근 가능
    console.log(this.dataMsg) // dataMsg
  }
}
</script>

<style scoped></style>
