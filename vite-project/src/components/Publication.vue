<template>
  <div>
    test {{title}}
  </div>
</template>

<script>
export default {
  name: "Publication",
  props: {
    title: String,
    authors: Array
  }
}
</script>

<style scoped>

</style>