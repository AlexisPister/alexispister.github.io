<template>
  <div id="main">
    <h1>Alexis Pister</h1>
    <img id="profile-picture" src="../assets/photo.jpg">
    <p> Doctoral Student at Aviz </p>

    <div class="icons">
      <a class="icon" href="alexis.pister@inria.fr">
        <i class="bx bx-mail-send"></i>
      </a>

      <a class="icon" href="https://scholar.google.com/citations?user=1V203DUAAAAJ&hl=fr&oi=ao">
        <i class="bx bxl-github"></i>
      </a>

      <a class="icon" href="https://scholar.google.com/citations?user=1V203DUAAAAJ&hl=fr&oi=ao">
        <i class="bx bxs-graduation"></i>
      </a>

      <a class="icon" href="https://twitter.com/apister2">
        <i class="bx bxl-twitter"></i>
      </a>

      <a class="icon" href="https://www.linkedin.com/in/alexis-pister-4748a4109/">
        <i class="bx bxl-linkedin"></i>
      </a>
    </div>
  </div>

</template>

<script>
import 'boxicons/css/boxicons.min.css';

export default {
  name: "PersonalProfil"
}
</script>

<style scoped>

#main {
  text-align: center;
}

#profile-picture {
  width: 80%;
  clip-path: circle(25% at 50% 30%);
  margin-bottom: -50%;
  margin-up: -10%;
}

a {
  color: inherit;
}

i {
  font-size: 190%;
}

i:hover {
  font-size: 210%;
}

</style>