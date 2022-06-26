<template>

  <div id="main">
    <Project name="ComBiNet" url="https://www.aviz.fr/Research/ComBiNet">
      <img src="../static/imgs/combinet.png">
    </Project>
    <Project name="PK-Clustering" url="https://aviz.fr/pkclustering">
      <img src="../static/imgs/PK-Clustering.png">
    </Project>
    <Project name="GraphletMatchMaker" url="https://graphletmatchmaker.github.io/">
      <img src="../static/imgs/vast-challenge.png">
    </Project>
    <Project name="TriSelectif" url="https://github.com/AlexisPister">
      <img src="../static/imgs/triSelectif.png">
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
  grid-template-rows: auto;
  /*grid-template-rows: 1fr;*/
  grid-column-gap: 20px;
  grid-row-gap: 20px;
  /*height: 100px;*/
}

img {
  object-fit: cover;
  border: 1px solid black;
  width: 100%;
  height: 80%
  /*height: 250px;*/
}

</style>