<template>

  <div id="main">
    <Project name="GraphletMatchMaker" url="https://graphletmatchmaker.github.io/" src="../assets/vast-challenge.png">
      <img src="../assets/vast-challenge.png">
    </Project>
    <Project name="GraphletMatchMaker" url="https://graphletmatchmaker.github.io/" src="../assets/vast-challenge.png">
      <img src="../assets/vast-challenge.png">
    </Project>
    <Project name="GraphletMatchMaker" url="https://graphletmatchmaker.github.io/" src="../assets/vast-challenge.png">
      <img src="../assets/vast-challenge.png">
    </Project>
    <Project name="GraphletMatchMaker" url="https://graphletmatchmaker.github.io/" src="../assets/vast-challenge.png">
      <img src="../assets/vast-challenge.png">
    </Project>
  </div>

</template>

<script>
import Project from "./Project.vue"

export default {
  name: "ProjectGrid",
  components: {Project}
}
</script>

<style scoped>
#main {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  /*grid-template-rows: 1fr;*/
  grid-column-gap: 20px;
  grid-row-gap: 20px;
}

img {
  object-fit: cover;
  border: 1px solid black;
  width: 100%;
  /*height: 250px;*/
}

</style>