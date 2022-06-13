<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import PersonalProfil from "./components/PersonalProfil.vue";
import Section from "./components/Section.vue";
import Project from "./components/Project.vue";
import ProjectGrid from "./components/ProjectGrid.vue";
import {onBeforeMount, ref} from "vue";
import Publication from "./components/Publication.vue";

let publications = ref();
onBeforeMount( async () => {
    let data = await fetch("../Exported Items.json")
    publications.value = await data.json();
    // console.log(publications)
    // publications = [1,2,3]
})

console.log(publications)
</script>

<template>
  <!--  <img alt="Vue logo" src="./assets/logo.png" />-->
  <!--  <HelloWorld msg="Super Message" />-->
  <div class="parent">
    <div id="personal" class="component">
      <personal-profil></personal-profil>
    </div>
    <div id="main-content" class="component">
      <Section title="Presentation">
        <div class="section">
          <p>Hello, I am Alexis Pister. I am a second year PhD in the fields of <strong>visualization</strong> and
            <strong>data mining</strong> applied to <strong>historical social networks</strong>
            at <a href="https://www.universite-paris-saclay.fr/">University Paris-Saclay</a> , more precisely at Inria
            Saclay (<a href="https://aviz.fr/">Aviz team</a>) and <a href="https://www.telecom-paris.fr/">Telecom
              Paris</a>, under the supervision of
            <a href="https://aviz.fr/~fekete/">Jean-Daniel Fekete</a> and <a
                href="https://perso.telecom-paristech.fr/cprieur/">Christophe Prieur</a>.</p>

          <p>My subject consists in developing visualization and analysis tools for <strong>community detection and
            pattern mining</strong> in historical dynamical social networks, with a strong focus on <strong>explainability
            and
            interactions.</strong></p>
        </div>
      </Section>

      <Section title="Education">
        <div class="section">
          <ul>
            <li> 2019: Master 2 of <strong>Artificial Intelligence</strong>, University Lyon I</li>
            <li> 2019: <strong>Bioinformatics and modeling engineering</strong> degree, INSA Lyon</li>
            <li> 2016: Bachelor of <strong>biology</strong> (2 years), Sorbonne University Paris</li>
          </ul>
          <p>You can see my professional curriculum <a target="_blank" rel="noopener noreferrer" href="CV.pdf">here</a>
            (1 page) and my academic one <a target="_blank" rel="noopener noreferrer" href="CV_Academique.pdf">here</a>.
          </p>
        </div>
      </Section>

      <Section title="Teaching">
        <div class="section">

          <ul>
            <li> 2020 - 2021: <strong>algorithmic and databases</strong> - engineer students, Polytech Paris-Saclay -
              64h
            </li>
            <li> 2019 - 2020: <strong>algorithmic and databases</strong> - engineer students, Polytech Paris-Saclay -
              64h
            </li>
          </ul>
        </div>
      </Section>

      <Section title="Awards">
        <div class="section">
          <ul>
            <li> VAST Mini-Challenge 1 Award: Outstanding Comprehensive Mini-Challenge 1 Solution <br/>
              GraphletMatchMaker: Visual Analytics Approaches to Graph Matching in Cybersecurity Communities <br/>
              Natkamon Tovanich, Alexis Pister, Gaëlle Richer, Paola Valdivia, Jean-Daniel Fekete, Christophe Prieur,
              Petra Isenberg
            </li>
          </ul>
        </div>
      </Section>

      <Section title="Publications">
        <ul>
        <li v-for="item in publications">
          <Publication :title="item.title"></Publication>
        </li>
        </ul>

<!--        <ul>-->
<!--        <li v-for="item in array">-->
<!--          <Publication :title="item"></Publication>-->
<!--        </li>-->
<!--        </ul>-->

      </Section>

      <Section title="Projects">
        <ProjectGrid></ProjectGrid>
      </Section>
    </div>
  </div>

</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  /*margin-top: 60px;*/
}

.section {
  padding-left: 20px;
}

.parent {
  display: grid;
  grid-template-columns: 2fr 7fr;
  grid-template-rows: 1fr;
  grid-column-gap: 23px;
  grid-row-gap: 0px;
  margin-left: 10vw;
  margin-right: 10vw;
  height: 100vh;
}

.component {
  /*border: 1px solid black;*/
  padding: 0 3%;
}

#personal {
  grid-area: 1 / 1 / 2 / 2;
}

#main-content {
  grid-area: 1 / 2 / 2 / 3;
}
</style>
