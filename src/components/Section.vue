<template>
  <h1 :id="title"> {{ title }} </h1>
  <slot id="test">
    Error
  </slot>

</template>

<script setup>
import {ref} from 'vue'

defineProps({
  title: String
})
</script>

<style scoped>

h1 {
  color: #000000;
  font-variant-caps: small-caps;
  font-weight: normal;
  display: table;

  background-image: linear-gradient(transparent 85%, #efa964 15%);
  //background-size: 100% 100%;
  //background-repeat: no-repeat;
  //background-position: top center;
}

</style>