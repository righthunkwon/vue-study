<template>
  <div>
    <button @click="handleOnClick('Hello vue3')">on click handler</button>
    <hr />
    <input type="text" @keyup="handleOnKeyup" />
  </div>
</template>

<script setup>
const handleOnClick = (msg) => {
  console.log('***************')
  console.log('msg', msg)
  console.log('event', event)
  console.log('event.target', event.target)
  console.log('event.target.tagName', event.target.tagName)
  console.log('***************')
}

const handleOnKeyup = (event) => {
  console.log('***************')
  console.log('event', event)
  console.log('event.key', event.key)
  console.log('event.target', event.target)
  console.log('event.target.tagName', event.target.tagName)
  console.log('***************')
}
</script>

<style lang="scss" scoped></style>
