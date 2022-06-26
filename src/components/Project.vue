<template>
  <div class=cell>
    <a v-bind:href="url">
      <slot>
      Error
      </slot>
      <p> {{name}} </p>
    </a>
  </div>
</template>

<script setup>

const props = defineProps({
  name: String,
  url: String,
  src: String
})
</script>

<style scoped>

div {
  text-align: center;
}

</style>