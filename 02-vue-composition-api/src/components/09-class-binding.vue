<template>
  <div>
    <h2>binding</h2>
    <button @click="toggleCaution">toggleCaution</button>
    <button @click="toggleWarning">toggleWarning</button>
    <div class="box"></div>
    <div class="box" :class="{ caution: isCaution }"></div>
    <div class="box" :class="{ warning: isWarning, important: isImportant }"></div>
    <div class="box" :class="classObj"></div>
  </div>
</template>

<script>
/**
 * Class & Style binding
 * : 클래스를 동적으로 바인딩하기 위해서는 :class(v-bind:class)와 같이 사용
 * : :class는 일반 class 속성과 공존 가능 / computed에도 바인딩 가능 / 객체와 배열의 형태로 사용 가능
 * : 스타일 역시 유사한 방식으로 동적으로 바인딩 가능
 *
 */

import { computed, ref } from 'vue'

export default {
  setup() {
    const isCaution = ref(true)
    const isWarning = ref(true)
    const isImportant = ref(true)

    const toggleCaution = () => {
      isCaution.value = !isCaution.value
    }
    const toggleWarning = () => {
      isWarning.value = !isWarning.value
    }

    const classObj = computed(() => {
      return {
        caution: false, // 노란색 내부
        warning: false, // 빨간색 내부
        important: true // 검은색 틀
      }
    })

    return { isCaution, isWarning, isImportant, toggleCaution, toggleWarning, classObj }
  }
}
</script>

<style scoped>
.box {
  margin-top: 4px;
  width: 200px;
  height: 200px;
  background-color: gray;
  border: 4cap;
  border-style: solid;
  border-color: gray;
}

.caution {
  background-color: yellow;
}

.warning {
  background-color: tomato;
}

.important {
  border: 4cap;
  border-style: solid;
  border-color: black;
}
</style>
