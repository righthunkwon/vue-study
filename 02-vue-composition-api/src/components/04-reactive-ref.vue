<template>
  <h1>반응형(Reactivity)</h1>
  <button @click="increment">Click {{ count }}</button>
  <button @click="incrementRef">Click ref {{ refCount }}</button>
  <button @click="incrementState">Click State {{ state.count }}</button>
  <button @click="incrementDeep">Click State Deep {{ state.deep.count }}</button>
</template>

<script>
/**
 * reactive()
 * : 객체타입에서만 동작
 * : 기본타입(number, string, boolean 등)을 반응형으로 만들고자 할 때는 ref 메소드를 활용
 *
 * ref()
 * : value 속성을 포함한 변이 가능한(mutable) 객체를 반환
 * : value 값은 ref 메서드에서 매개변수로 받은 값을 가지고 있음
 * : 해당 객체 내부에는 value라는 하나의 속성만 포함하며 반응형 참조의 역할 수행
 * : 자바스크립트 내부에서는 value 속성을 명시해야하지만, 템플릿에서는 자동으로 value 속성을 대입하므로 생략
 *
 * 결론
 * : 팀 내 컨벤션에 따라서 사용하는 게 좋지만, 기본적으로는 일관성은 조금 부족할지라도
 * : .value를 명시하여 값을 표기하는 ref 사용을 권장
 *
 */
import { ref, reactive } from 'vue'

export default {
  setup() {
    let count = reactive(0) // [WARN]: value cannot be made reactive
    const refCount = ref(0)
    const state = reactive({
      count: 0,
      deep: {
        count: 0
      }
    })

    const increment = () => {
      count += 1
    }
    const incrementRef = () => {
      refCount.value += 1
    }
    const incrementState = () => {
      state.count += 1
    }
    const incrementDeep = () => {
      state.deep.count += 1
    }

    return { count, refCount, state, increment, incrementRef, incrementState, incrementDeep }
  }
}
</script>

<style scoped></style>

<!-- 1. ref 사용 -->
<!-- 

import { ref } from "vue";

export default {
  setup() {
    const person1 = ref({ name: "Hong Kil Dong", age: 30 });

    const updatePerson = () => {
      // ref로 감싼 date는 value로 접근한 뒤 값에 접근
      person1.value.age = 50;
    };

    return {
      person1,
      updatePerson,
    };
  },
}; 

-->

<!-- 2. reactive 사용 -->
<!-- 

import { reactive } from "vue";

export default {
  setup() {
    const person1 = reactive({ name: "Hong Kil Dong", age: 30 });

    const updatePerson = () => {
      // reactive로 감싼 data는 바로 접근한 뒤 값에 접근
      person1.age = 50;
    };

    return {
      person1,
      updatePerson,
    };
  },
}; 

-->
