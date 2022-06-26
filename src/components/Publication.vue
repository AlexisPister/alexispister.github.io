<template>
  <div id="title">
    {{ title}}<span v-if="type == 'award'">, {{ year }}</span>
  </div>


  <span v-for="(author, index) in authors">
  <span v-if="index !== 0">, </span>
    <em>
    <span v-if="author.family === 'Pister'" class="me-author">
      <strong>{{ author.given }} {{ author.family }}</strong>
    </span>
    <span v-else>
    {{ author.given }} {{ author.family }}
    </span>
      </em>
  </span>

  <div v-if="type == null" class="venue">
    {{ venue }},  {{ year }}
  </div>
</template>

<script>
export default {
  name: "Publication",
  props: {
    title: String,
    authors: Array,
    venue: String,
    year: Number,
    type: String
  }
}
</script>

<style scoped>

.venue {
  color: gray;
}

</style>