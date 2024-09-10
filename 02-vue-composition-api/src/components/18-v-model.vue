<template>
  <h2>1. input value</h2>
  <div>
    <!-- v-model -->
    <input type="text" v-model="inputValue1" />
    <!-- event -->
    <input
      type="text"
      :value="inputValue2"
      @input="(event) => (inputValue2 = event.target.value)"
    />
  </div>
  <div>inputValue1: {{ inputValue1 }}</div>
  <div>inputValue2: {{ inputValue2 }}</div>
  <hr />

  <h2>2. checkbox value</h2>
  <!-- v-model -->
  <label for="checkbox1">{{ checkboxValue1 }}</label>
  <input type="checkbox" id="checkbox1" v-model="checkboxValue1" />
  <!-- event -->
  <label for="checkbox2">{{ checkboxValue2 }}</label>
  <input
    type="checkbox"
    id="checkbox2"
    :checked="checkboxValue2"
    @change="(event) => (checkboxValue2 = event.target.checked)"
  />
  <hr />

  <h2>3. radio value</h2>
  <div>radioValue: {{ radioValue }}</div>
  <!-- v-model -->
  <label>
    A
    <input type="radio" name="type" value="A" v-model="radioValue" />
  </label>
  <!-- event -->
  <label>
    B
    <input
      type="radio"
      name="type"
      value="B"
      :checked="radioValue === 'B'"
      @change="(event) => (radioValue = event.target.value)"
    />
  </label>
  <hr />

  <h2>4. select value</h2>
  <!-- v-model -->
  <select v-model="selectValue">
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="javascript">JavaScript</option>
  </select>
  <!-- event -->
  <select @change="(event) => (selectValue = event.target.value)">
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="javascript">JavaScript</option>
  </select>
  <div>{{ selectValue }}</div>
</template>

<script setup>
/**
 * 양방향 바인딩 구현 방법
 *  - 1. v-model 활용
 *  - 2. event 객체 활용
 */
import { ref } from 'vue'

const inputValue1 = ref('')
const inputValue2 = ref('')
const checkboxValue1 = ref(true)
const checkboxValue2 = ref(true)
const radioValue = ref('A')
const selectValue = ref('html')
</script>

<style lang="scss" scoped></style>
