<script>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import PersonalProfil from "./components/PersonalProfil.vue";
import Section from "./components/Section.vue";
import Project from "./components/Project.vue";
import ProjectGrid from "./components/ProjectGrid.vue";
import Publication from "./components/Publication.vue";
import Publications from "./components/Publications.vue";
import {groupBy} from "lodash/collection";
import {pubTypes, publicationsTypesEnum} from "./js/utils.js";

import CV from './static/CV.pdf';
import publicationsList from "./static/Exported Items.json"

// let publications = ref();
// onBeforeMount( async () => {
//     let data = await fetch("../Exported Items.json")
//     publications.value = await data.json();
// })

export default {
  name: "App",
  components: {Publication, ProjectGrid, Project, PersonalProfil, Section, Publications},
  props: {
    title: String,
    authors: Array
  },
  data() {
    return {
      publications: null,
      cv: CV
    }
  },
  async created() {
    // this.publications = await fetch("../Exported Items.json").then(data => data.json());
    this.publications = publicationsList;
  },
  computed: {
    publicationsProcessed() {
      if (this.publications) {
        this.publications.forEach(pub => {
          pub.type = this.findPubType(pub);
        })

        // TODO: I deleted reports for now for duplication of VAST Challenge, may cause issues later
        this.publications = this.publications.filter(pub => pub.type != "Reports")

        let pubs = groupBy(this.publications, d => d.type)

        return pubs
      } else {
        return null;
      }
    },
    VASTChallengePublication() {
      return this.publications ? this.publications.filter(pub => pub.DOI == "10.1109/MCG.2021.3091955")[0] : {author: null};
    }
  },
  methods: {
    findPubType(publication) {
      if (publication["publisher"] == "arXiv") {
        return publicationsTypesEnum.Preprint;
      } else if (publication["note"] && publication.note.toLowerCase().includes("poster")) {
        return publicationsTypesEnum.Posters;
      } else {
        return pubTypes[publication.type];
      }
    }
  }
}

</script>

<template>
  <!--  <img alt="Vue logo" src="./static/logo.png" />-->
  <!--  <HelloWorld msg="Super Message" />-->
  <div class="parent">
    <div id="personal" class="component">
      <personal-profil></personal-profil>
    </div>

    <div id="main-content" class="component">
      <Section title="Presentation">
        <div class="section">
          <p>Hello, I am Alexis Pister. I am a third year PhD student in the field of <strong>Visual Analytics</strong> applied to <strong>historical social networks</strong>
            at <a href="https://www.universite-paris-saclay.fr/">University Paris-Saclay</a>, specifically at Inria
            Saclay (<a href="https://aviz.fr/">Aviz team</a>) and <a href="https://www.telecom-paris.fr/">Telecom
              Paris</a>, under the supervision of
            <a href="https://aviz.fr/~fekete/">Jean-Daniel Fekete</a> and <a
                href="https://perso.telecom-paristech.fr/cprieur/">Christophe Prieur</a>.</p>

          <p>I work on developing dynamic and multivariate social network visual analytics systems to explore historical data, with a strong focus on <strong>explainability and interactions.</strong></p>

          <p>I am interested in social network visual analytics, temporal hypergraph visualization and graph drawing.</p>

        </div>
      </Section>

      <Section title="Education">
        <div class="section">
          <ul>
            <li> 2018-2019: Master 2 of <strong>Artificial Intelligence</strong>, University Lyon I</li>
            <li> 2016-2019: <strong>Bioinformatics and Modeling Engineering</strong> Degree, INSA Lyon</li>
            <li> 2014-2016: Bachelor of <strong>Biology</strong> (2 years), Sorbonne University Paris</li>
          </ul>
          <p>
<!--            You can see my professional curriculum <a target="_blank" rel="noopener noreferrer" href="./static/CV.pdf">here</a>.-->
            You can see my professional curriculum <a target="_blank" rel="noopener noreferrer" :href="cv">here</a>.
          </p>
        </div>
      </Section>

      <Section title="Teaching">
        <div class="section">
          <ul>
            <li> 2020-2021: <strong>Algorithms and Databases</strong> - Engineer students, Polytech Paris-Saclay -
              64h
            </li>
            <li> 2019-2020: <strong>Algorithms and Databases</strong> - Engineer students, Polytech Paris-Saclay -
              64h
            </li>
          </ul>
        </div>
      </Section>

      <Section title="Awards">
        <div class="section">
          <!--          <ul>-->
          <!--            <li> VAST Mini-Challenge 1 Award: Outstanding Comprehensive Mini-Challenge 1 Solution <br/>-->
          <!--              GraphletMatchMaker: Visual Analytics Approaches to Graph Matching in Cybersecurity Communities <br/>-->
          <!--              Natkamon Tovanich, Alexis Pister, Gaëlle Richer, Paola Valdivia, Jean-Daniel Fekete, Christophe Prieur,-->
          <!--              Petra Isenberg-->
          <!--            </li>-->
          <!--          </ul>-->
          <ul>
            <Publication title="VAST Mini-Challenge 1 Award: Outstanding Comprehensive Mini-Challenge 1 Solution"
                         :authors="VASTChallengePublication.author" year="2020" venue="" type="award"></Publication>
          </ul>
        </div>
      </Section>

      <Section title="Publications">
        <div class="section">
          <Publications v-if="publications" :publicationsByType="publicationsProcessed">
          </Publications>
        </div>
      </Section>

      <Section title="Projects">
        <div class="section">
          <ProjectGrid></ProjectGrid>
        </div>
      </Section>

      <Section title="Talks">
        <div class="section">
          <ul>
            <li>
              <a href="http://dahlia.egc.asso.fr/atelierDAHLIA-EGC2022.html">Requêtes et Comparaisons de Réseaux Sociaux Bipartis Multivariés Dynamiques</a><br/>
              Knowledge Extraction and Managment Conference<br>
              Virtual, January, 24nd 2022
            </li>
            <li>
              <a href="http://hnr2021.historicalnetworkresearch.org/?page_id=349">PK-Clustering: Integrating Prior Knowledge in Mixed-Initiative Social Network Clustering</a><br>
              Historical Networks Conference (HNR)<br>
              Virtual, August, 2nd 2021
            </li>
            <li>
              <a href="https://jdse-paris.github.io/jDSE2021/">PK-Clustering: Integrating Prior Knowledge in Mixed-Initiative Social Network Clustering</a><br>
              Junior Conference on Data Science and Engineering (JDSE)<br>
              Saclay, February, 2nd 2021
            </li>
            <li>
              <a href="https://www.ined.fr/en/news/scientific-meetings/ined_mondays/integrer-les-connaissances-prealables-pour-le-clustering-de-reseaux-sociaux">
              Intégrer les connaissances préalables pour le clustering de réseaux sociaux
            </a><br>
              INED
              <br> Paris, November, 9th 2020
            </li>
          </ul>
        </div>
      </Section>

      <Section title="Volunteering">
        <div class="section">
          <ul>
            <li>EuroVis 2022</li>
            <li>VIS 2020 (Virtual)</li>
          </ul>
        </div>
      </Section>
    </div>
  </div>

</template>

<style>
body {
  margin: 0px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  /*margin-top: 60px;*/
}

.styled {
  color: #000000;
  font-variant-caps: small-caps;
  font-weight: normal;
}

li{
  margin: 4px 0;
}

.section {
  padding-left: 8px;
}

.parent {
  display: grid;
  grid-template-columns: 2fr 7fr;
  grid-template-rows: 1fr;
  grid-column-gap: 23px;
  grid-row-gap: 0px;
  margin-left: 10vw;
  margin-right: 10vw;
  /*height: 100vh;*/
  align-items: start;
}

.component {
  /*border: 1px solid black;*/
  padding: 0 3%;
  padding-top: 15px;
  /*margin: 10%;*/
}

#personal {
  grid-area: 1 / 1 / 2 / 2;
  position: sticky;
  top: 0;
  /*align-self: start;*/
  /*align-self: stretch;*/
}

#main-content {
  grid-area: 1 / 2 / 2 / 3;
}
</style>
