<template>
  <ul v-if="publicationsByType">
    <div v-for="(publications, type) in publicationsByType">
      <h2 id="publication-type-title"> {{ type }}</h2>
      <li v-for="item in publications">
        <Publication :title="item.title" :authors="item.author" :venue="item.venue" :year="item.year"></Publication>
      </li>
    </div>
  </ul>
</template>

<script>
import Publication from "./Publication.vue";

export default {
  name: "Publications",
  props: {
    publicationsByType: Array
  },
  components: {Publication},
  mounted() {
    // sort by time
    this.sortByTime();

    Object.values(this.publicationsByType).reduce((a, b) => a.concat(b)).forEach(pub => {
      this.processPub(pub)
    })
  },
  methods: {
    sortByTime() {
      Object.values(this.publicationsByType).forEach(pubs => {
        pubs.sort((a,b) => {
          return b["issued"]["date-parts"][0][0] - a["issued"]["date-parts"][0][0]
        })
      })
    },
    processPub(pub) {
      let venue;
      if (pub["container-title"]) {
        venue = pub["container-title"];
      } else if (pub["publisher"]){
        venue = pub["publisher"];
      } else if (pub["event"]) {
        venue = pub["event"];
      }
      pub.venue = venue;
      pub.year = pub["issued"]["date-parts"][0][0]
    }
  }
}
</script>

<style scoped>

/*li {*/
/*  padding: 3px;*/
/*}*/

#publication-type-title {
  color: #000000;
  font-variant-caps: small-caps;
  font-weight: normal;
}

</style>