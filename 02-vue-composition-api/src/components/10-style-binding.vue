<template>
  <div>
    <div :style="styleObj">
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Saepe facilis quam soluta debitis
      voluptatibus consequatur minus? Voluptatum laboriosam ullam aut cumque quo maxime, dolor
      eveniet, expedita, non quibusdam exercitationem in?
    </div>
  </div>
</template>

<script>
import { reactive } from 'vue'

export default {
  setup() {
    const styleObj = reactive({
      color: 'white',
      fontSize: '16px',
      backgroundColor: 'cornflowerblue'
    })

    return { styleObj }
  }
}
</script>

<style lang="scss" scoped></style>
