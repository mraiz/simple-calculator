<template>
  <div id="app">
    <div id="nav">
      <div class="app-title">Aplikasi Kalkulator Sederhana</div>
      <div class="author">Author : Abdul Aziz Laia | Repo <a href="https://github.com/mraiz/simple-calculator">Link Here </a> </div>
    </div>
    
    <router-view />
  </div>
</template>

<style>
body {
  background: #e9fffd;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  font-size: 18px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

.app-title {
  font-weight: bold;
}

.author {
  font-size: 14px;
  color: #acacac;
}

.author a{
  text-decoration: none;
  color: inherit;
}
</style>
