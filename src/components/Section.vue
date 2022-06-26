<template>
  <h1 :id="title"> {{ title }} </h1>
  <slot id="test">
    Error
  </slot>

</template>

<script setup>
import { ref } from 'vue'

defineProps({
  title: String
})

const count = ref(0)
</script>

<style scoped>

h1 {
  color: #000000;
  font-variant-caps: small-caps;
  font-weight:normal;
}

</style>