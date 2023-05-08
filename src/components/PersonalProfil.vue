<template>
  <div id="main">
    <h1><span id="name">Alexis Pister</span></h1>
<!--    <img id="profile-picture" src="../static/photo.jpg">-->
    <img id="profile-picture" src="../static/Moi.jpg">

    <div class="icons">
      <a class="icon" href="alexis.pister@hotmail.com">
        <i class="bx bx-mail-send"></i>
      </a>

      <a class="icon" href="https://github.com/AlexisPister/">
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

    <div id="nav-bar" class="styled">
      <a href="#Presentation"> Presentation </a>
      <a href="#Education"> Education </a>
      <a href="#Teaching"> Teaching </a>
      <a href="#Awards"> Awards </a>
      <a href="#Publications"> Publications </a>
      <a href="#Projects"> Projects </a>
      <a href="#Talks"> Talks </a>
      <a href="#Volunteering"> Volunteering </a>
      <a href="#Reviewing"> Reviewing </a>
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
  /*position: fixed;*/
}

#name {
  background-image: linear-gradient(transparent 78%, #efa964 50%);
}

h1 {
  margin-bottom: 6%;
  /*margin-bottom: 1%;*/
}

#profile-picture {
  width: 65%;
  /*width: 80%;*/
  clip-path: circle(35% at 50% 30%);
  /*clip-path: circle(25% at 50% 30%);*/
  margin-bottom: -26%;
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

#nav-bar {
  display: flex;
  flex-direction: column;
  margin-top: 8%;
}

</style>