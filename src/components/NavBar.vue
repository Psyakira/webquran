<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <a class="navbar-brand">QuranWeb</a>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/">Welcome</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/home">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/about">About</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <router-view/>
  <p class="fixed-bottom">CopyRight by Syakira</p>
</template>

<script>
export default {
  name: "NavBar"
}
</script>

<style scoped>
.navbar{
  color: black;
  padding: 0;
  margin-bottom: 10px;
  margin-top: 0px;
  background-color: cadetblue;
}
li{
  list-style: none;
  text-decoration: none;
}
.container-fluid{
  background-color: cadetblue
}
.fixed-bottom{
  color: cadetblue;
}
.navbar-brand{
  font-family: "Bodoni MT Black";
  font-size: 30px;
}
p{
  margin: 0px;
  padding: 0px;
}
</style>