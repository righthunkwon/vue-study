<template>
  <div>
    <ul>
      <li v-for="(lang, index) in langs" :key="lang.id">
        <div>No: {{ index }}</div>
        <div>ID: {{ lang.id }}</div>
        <div>Name: {{ lang.name }}</div>
      </li>
    </ul>
    <hr />
    <ul>
      <li v-for="(value, key, index) in myObj" :key="key">{{ index }}-{{ key }}-{{ value }}</li>
    </ul>
  </div>
</template>

<script>
import { reactive } from 'vue'

export default {
  setup() {
    const langs = reactive([
      {
        id: 1,
        name: 'Java'
      },
      {
        id: 2,
        name: 'HTML'
      },
      {
        id: 3,
        name: 'CSS'
      },
      {
        id: 4,
        name: 'JavaScript'
      }
    ])

    const myObj = reactive({
      name: 'myObj',
      type: 'object',
      publishedAt: '2024-08-07'
    })

    return { langs, myObj }
  }
}
</script>

<style lang="scss" scoped></style>
