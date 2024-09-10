<template>
  <div>
    <!-- slot1 -->
    <FancyButton>Fancy Click</FancyButton>
    <br />

    <!-- slot2 (default) -->
    <FancyButton></FancyButton>
    <br />

    <!-- slot3 (named slot) -->
    <BaseCard>
      <template #header>#Header data</template>
      <template #content>#Content data</template>
      <template #footer>#Footer data</template>
      <template #default="{ childRef1, childRef2 }"
        >#default / {{ parentRef }} / {{ childRef1 }} / {{ childRef2 }}</template
      >
    </BaseCard>
    <br />

    <!-- slot4 (named slot) -->
    <!-- 내부 데이터가 없는 요소도 렌더링 중(ex. header, footer) -->
    <DemoCard1>
      <template #content>#Content data</template>
    </DemoCard1>
    <br />

    <!-- slot5 (named slot) -->
    <!-- slot의 부모에 v-if="$slots.name"을 정의하여 slot 내부 데이터가 없는 요소는 렌더링하지 않음 -->
    <DemoCard2>
      <template #content>#Content data</template>
    </DemoCard2>
    <br />
  </div>
</template>

<script setup>
import BaseCard from '@/components/BaseCard.vue'
import DemoCard1 from '@/components/DemoCard1.vue'
import DemoCard2 from '@/components/DemoCard2.vue'
import FancyButton from '@/components/FancyButton.vue'
import { ref } from 'vue'

const parentRef = ref('부모 데이터')

/**
 *  v-slot(#)
 *  : 자식에서 정의하며, 부모에서 전달한 값을 활용
 *  : slot에는 텍스트, HTML, 컴포넌트 등 다양한 요소가 올 수 있음
 *  : 자식에서는 <slot></slot>의 형태로 사용하고,
 *    부모에서는 v-slot:전달인자 혹은 #전달인자의 형태로 사용 (*template 내부에 위치)
 *
 *  : slot 요소에 이름을 부여하여 여러 slot을 정의하고 구분 가능
 *  : 자식에서 slot에 name 속성을 지정하여 이름을 부여 (*name이 없는 slot은 default로 취급)
 *
 *  : 기본적으로 부모 컴포넌트에서는 자식 컴포넌트의 데이터에 접근할 수 없지만,
 *    자식의 slot 요소에서 props를 전달하는 것처럼 속성을 정의함으로써 자식 컴포넌트에서 부모 컴포넌트로
 *    데이터 전달 가능
 *
 *  : v-if="$slots.name"의 형태로 렌더링을 원하지 않는 요소를 렌더링하지 않을 수 있음
 */
</script>

<style scoped></style>
