<template>
  <div>
    <div :style="styleObj">
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Saepe facilis quam soluta debitis
      voluptatibus consequatur minus? Voluptatum laboriosam ullam aut cumque quo maxime, dolor
      eveniet, expedita, non quibusdam exercitationem in?
    </div>
    <button @click="fontSize++">+</button>
    <button @click="fontSize--">-</button>
  </div>
</template>

<script>
import { ref, computed } from 'vue'

export default {
  setup() {
    const fontSize = ref(14)
    const styleObj = computed(() => {
      return {
        color: 'white',
        fontSize: fontSize.value + 'px',
        backgroundColor: 'cornflowerblue'
      }
    })

    return { fontSize, styleObj }
  }
}
</script>

<style lang="scss" scoped></style>
